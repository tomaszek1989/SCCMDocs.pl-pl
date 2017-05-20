---
title: "Planowanie ról systemu lokacji | Dokumentacja firmy Microsoft"
description: "Podczas planowania hierarchii programu System Center Configuration Manager, należy rozważyć serwerów systemu lokacji i ról systemu lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a93ea730c39cce9dc46036f5aa6ece4a62679d0f
ms.openlocfilehash: 0d16d362b798c194645f987088ba8a95a7be3f19
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-site-system-servers-and-site-system-roles-for-system-center-configuration-manager"></a>Planowanie serwerów i ról systemu lokacji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Każda lokacja programu System Center Configuration Manager można zainstalować obejmuje serwer lokacji, który jest **serwera systemu lokacji**. Lokacja może obejmować także dodatkowe serwery systemu lokacji na komputerach zdalnych względem serwera lokacji. Serwery systemu lokacji (serwer lokacji lub zdalny serwer systemu lokacji) obsługują **role systemu lokacji**.


##  <a name="bkmk_siteservers"></a> Serwery systemu lokacji  
 Podczas instalowania roli systemu lokacji na komputerze z tego komputera staje się serwerem systemu lokacji. W każdej lokacji można zainstalować jeden lub więcej dodatkowych serwerów systemu lokacji. Istnieje również możliwość nie zainstaluj dodatkowe serwery systemu lokacji, a następnie uruchom wszystkie role systemu lokacji bezpośrednio na komputerze serwera lokacji. Każdy serwer systemu lokacji obsługuje jedną lub więcej ról systemu lokacji. Dodatkowe serwery może ułatwić rozszerzyć możliwości i wydajność lokacji udostępniając obciążenie związane z przetwarzaniem Procesora na serwerze, że role systemu lokacji.  

 Podczas wybierania dodanie serwera systemu lokacji, upewnij się, że serwer spełnia wymagania wstępne dotyczące zamierzonego użycia. Istnieje również dobrze jest dodać go do lokalizacji sieciowej, która ma wystarczającą przepustowość do komunikowania się z oczekiwanym punktów końcowych, łącznie z serwera lokacji, zasobów domeny, oparte na chmurze lokalizacji, serwery systemu lokacji i klientów).  

 Konfigurowanie serwera systemu lokacji z serwera proxy do użytku przez role systemu lokacji, zobacz [role systemu lokacji używających serwera proxy](#bkmk_proxy).  

##  <a name="bkmk_planroles"></a> Site system roles  
 Role systemu lokacji są instalowane na komputerze, aby zapewnić lokacji dodatkowe możliwości. Przykłady obejmują:  

-   Tak, aby witryna może obsługiwać więcej urządzeń obsługiwanych pojemności lokacji do punktów dodatkowe zarządzania.  

-   Punkty dystrybucji dodatkowe rozszerzenia infrastrukturę zawartości usprawnianie dystrybucją zawartości do urządzeń i użytkowników.  

-   Jeden lub więcej ról systemu lokacji właściwych dla funkcji. Na przykład punkt aktualizacji oprogramowania umożliwia zarządzanie aktualizacji oprogramowania dla zarządzanych urządzeń lub punkt usług raportowania umożliwia uruchamianie raportów, aby monitorować i zapoznać się lub udostępniać informacje o instalacji.  


Różnych lokacji programu Configuration Manager może obsługiwać różne zestawy ról systemu lokacji. Zestaw obsługiwanych ról systemu lokacji zależy od typu witryny (centralnej lokacji administracyjnej, lokacji głównej lub dodatkowej lokacji). Topologia hierarchii może ograniczać rozmieszczanie niektórych ról w określonych typach lokacji. Na przykład punkt połączenia usługi jest obsługiwany tylko w lokacji najwyższego poziomu w hierarchii, która może być centralną lokacją administracyjną lub autonomiczną lokacją główną. Ta rola nie jest obsługiwana w podrzędnej lokacji głównej ani w lokacjach dodatkowych.  

Po zainstalowaniu lokacji, należy przenieść lokalizację niektóre role systemu lokacji z lokalizacji domyślnej na serwerze lokacji do innego serwera. Na przykład dotyczy to punkt zarządzania lub punkt dystrybucji, w którym instalowane domyślnie na serwerze lokacji głównej lub dodatkowej. Można także zainstalować dodatkowe wystąpienia niektóre role systemu lokacji, aby rozszerzyć możliwości witryny (utworzyć więcej usług dla klientów) i w celu spełnienia wymagań biznesowych. Niektóre role są wymagane, a inne są opcjonalne.  

-   **Serwer lokacji programu Configuration Manager.** Ta rola identyfikuje serwer, na którym uruchomiono Instalatora programu Configuration Manager do zainstalowania lokacji lub serwer, na którym jest instalowana lokacji dodatkowej. Tej roli nie można przenieść ani odinstalować do momentu odinstalowania lokacji.  

-   **System lokacji programu Configuration Manager.** Ta rola jest przypisywana do każdego komputera, na którym można zainstalować lokacji lub zainstalować rolę systemu lokacji. Tej roli nie można przenieść ani odinstalować do momentu usunięcia z komputera ostatniej roli systemu lokacji.  

-   **Rola systemu lokacji składnika programu Configuration Manager.** Ta rola identyfikuje systemu lokacji uruchomione jest wystąpienie usługi głównej programu SMS, która jest wymagana do obsługi innych ról, takich jak punkty zarządzania. Tej roli nie można przenieść ani odinstalować do momentu usunięcia z komputera ostatniej stosownej roli systemu lokacji.  

-   **Serwer bazy danych lokacji programu Configuration Manager.** Ta rola jest przypisywana do serwerów systemu lokacji, które zawierają wystąpienia bazy danych lokacji dla lokacji. Ta rola tylko można przenieść na nowy serwer, modyfikując lokacji do używania innego wystąpienia programu SQL Server do obsługi bazy danych lokacji.  

-   **Dostawca programu SMS.** Rola Dostawca programu SMS jest przypisany do każdego komputera, który obsługuje wystąpienie dostawcy programu SMS, interfejs pomiędzy konsolą programu Configuration Manager i bazy danych lokacji. Domyślnie ta rola automatycznie zainstaluje na serwerze lokacji centralnej lokacji administracyjnej i lokacji głównych. Można zainstalować dodatkowe wystąpienia w każdej lokacji w celu zapewnienia dostępu użytkownikom administracyjnym dodatkowe.  

     Aby zainstalować dodatkowych dostawców, należy uruchomić Instalatora programu Configuration Manager do [zarządzania dostawcą programu SMS](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider). Następnie można zainstalować dodatkowych dostawców na dodatkowych komputerach. Na komputerze można zainstalować tylko jedno wystąpienie dostawcy programu SMS, a komputer ten musi być w tej samej domenie co serwer lokacji.  

-   **Punkt usługi sieci web katalogu aplikacji.** Rola systemu lokacji, która dostarcza do witryny sieci Web katalogu aplikacji informacje o oprogramowaniu z biblioteki oprogramowania. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

-   **Punkt witryny sieci Web katalogu aplikacji.** Rola systemu lokacji, która dostarcza użytkownikom listę dostępnego oprogramowania z katalogu aplikacji. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

     Jeżeli katalog aplikacji obsługuje komputery klienckie w Internecie, jest ze względów bezpieczeństwa zainstalować punkt witryny sieci Web katalogu aplikacji w sieci obwodowej zabezpieczeń oraz zainstalować punkt usługi sieci web katalogu aplikacji w sieci intranet.  

-   **Punkt synchronizacji analizy zasobów.** Rola systemu lokacji, który łączy do firmy Microsoft, aby pobrać informacje o katalogu analizy zasobów. Ta rola przekazuje również tytułów bez kategorii, które mogą zostać uwzględnione w przyszłości w katalogu. Hierarchia obsługuje tylko jedno wystąpienie tej roli, i który musi być w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej). Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej i zainstalować go w witrynie Administracja centralna.   Aby uzyskać więcej informacji, zobacz [Analiza zasobów w programie System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Punkt rejestracji certyfikatu.** Rola systemu lokacji, który komunikuje się z serwerem z uruchomioną usługą rejestracji urządzeń sieciowych. Ta rola zarządza żądaniami certyfikatów urządzeń używających prostego protokołu rejestrowania certyfikatów (SCEP). Ta rola jest obsługiwana tylko w lokacjach głównych i centralnej lokacji administracyjnej.

     Mimo że jeden punkt rejestracji certyfikatu może zapewniać funkcje w całej hierarchii, można zainstalować wiele wystąpień tej roli w lokacji oraz w wielu lokacjach w tej samej hierarchii. Może to ułatwić z równoważeniem obciążenia. Jeśli w hierarchii istnieje wiele wystąpień, klienci są losowo przydzielani do jednego z punktów rejestracji certyfikatu.  

     Każdy punkt rejestracji certyfikatu wymaga dostępu do oddzielnego wystąpienia usługi rejestracji urządzeń sieciowych. Nie można skonfigurować, aby dwa lub więcej punktów rejestracji certyfikatu korzystało z tej samej usługi rejestracji urządzeń sieciowych. Ponadto punktu rejestracji certyfikatu nie można zainstalować na serwerze z uruchomioną usługą rejestracji urządzeń sieciowych.  

- **Punkt łącznik chmury zarządzania bramy.** Rola systemu lokacji do komunikowania się z [brama zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway).

-   **Punkt dystrybucji.** Rola systemu lokacji zawierająca pliki źródłowe do pobrania przez klientów, takie jak zawartość aplikacji, pakiety oprogramowania, aktualizacje oprogramowania, obrazy systemu operacyjnego i obrazy rozruchowe. Domyślnie ta rola jest instalowana na komputerze serwera lokacji nowych lokacji głównych i dodatkowych w momencie instalacji lokacji. Ta rola nie jest obsługiwane w witrynie Administracja centralna. Można zainstalować wiele wystąpień tej roli w obsługiwanej lokacji oraz w wielu lokacjach w tej samej hierarchii. Aby uzyskać więcej informacji, zobacz temat [Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) oraz [Zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   **Rezerwowy punkt stanu.** Rola systemu lokacji, która pomaga monitorować instalacje klienta i identyfikować klientów, które są zarządzane, którzy nie mogą komunikować się ze swoim punktem zarządzania. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji i w wielu lokacjach w tej samej hierarchii. Aby uzyskać więcej informacji, zobacz [Scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).


-   **Punkt ochrony punktu końcowego.** Rola systemu lokacji, która korzysta z programu Configuration Manager do akceptowania postanowień licencyjnych programu Endpoint Protection i konfigurowania domyślnego członkostwa w usłudze ochrony chmury. Hierarchia obsługuje tylko jedno wystąpienie tej roli, i który musi być w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej). Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej i zainstalować go w witrynie Administracja centralna. Aby uzyskać więcej informacji, zobacz [Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

-   **Punkt rejestracji.** Rola systemu lokacji, która korzysta z certyfikatów PKI programu Configuration Manager do rejestrowania urządzeń przenośnych i komputerów Mac. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

     Jeśli użytkownik rejestruje urządzenia przenośnego za pomocą programu Configuration Manager, a konto użytkownika usługi Active Directory znajduje się w niezaufanym lesie serwera lokacji, należy zainstalować punkt rejestracji w lesie użytkownika. Następnie użytkownik może zostać uwierzytelniony.  

-   **Punkt proxy rejestracji.** Rola systemu lokacji, która zarządza żądaniami rejestrowania programu Configuration Manager z urządzeń przenośnych i komputerów Mac. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

     W przypadku obsługi urządzeń przenośnych w Internecie, zainstalować punkt proxy rejestracji w sieci obwodowej zabezpieczeń i zainstalować punkt rejestracyjny w intranecie.  

-   **Łącznik serwera Exchange.** Aby uzyskać informacje o tej roli, zobacz [zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)  

-   **Punkt zarządzania.** Rola systemu lokacji, która dostarcza klientom informacji o lokalizacji zasad i usługi oraz odbiera od klientów dane konfiguracji.  

    Domyślnie ta rola jest instalowana na komputerze serwera lokacji nowych lokacji głównych i dodatkowych w momencie instalacji lokacji. Lokacje główne obsługują wiele wystąpień tej roli. Lokacje dodatkowe obsługują pojedynczy punkt zarządzania, aby zapewnia lokalny punkt kontaktu dla klientów w celu uzyskania komputerów i użytkowników zasady (punkt zarządzania w lokacji dodatkowej jest określany jako punkt zarządzania proxy).  

     Punkty zarządzania można skonfigurować do obsługi protokołu HTTP lub HTTPs, a także do obsługi urządzeń przenośnych, którymi można zarządzać za pomocą funkcji zarządzania urządzeniami System Center Configuration Manager lokalnych Mobile. Możliwe jest użycie [replik bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md), aby zmniejszyć obciążenie procesora CPU serwera bazy danych lokacji powodowanego przez punkty zarządzania obsługujące żądania od klientów.  

-   **Punkt usług raportowania.** Rola systemu lokacji zintegrowana z SQL Server Reporting Services do tworzenia i zarządzania raportami programu Configuration Manager. Ta rola jest obsługiwana w lokacji głównej i centralnej lokacji administracyjnej i można zainstalować wiele wystąpień tej roli w obsługiwanych lokacji. Aby uzyskać więcej informacji, zobacz [Planowanie raportowania w programie System Center Configuration Manager](../../../core/servers/manage/planning-for-reporting.md).  

-   **Punkt połączenia usługi.** Rola systemu lokacji, który umożliwia zarządzanie urządzeniami przenośnymi za pomocą programu Microsoft Intune i dla lokalnego zarządzania urządzeniami przenośnymi. Ta rola również przekazywania danych do użycia z witryny i jest wymagany w celu udostępnienia aktualizacji programu Configuration Manager w konsoli programu Configuration Manager. Hierarchia obsługuje tylko jedno wystąpienie tej roli, i który musi być w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej). Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej i zainstalować go w witrynie Administracja centralna. Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   **Punkt aktualizacji oprogramowania.** Rola systemu lokacji zintegrowana z systemu Windows Server Update Services (WSUS) w celu udostępnienia aktualizacji oprogramowania do klientów programu Configuration Manager. Ta rola jest obsługiwana we wszystkich lokacjach:  

    -   Zainstaluj ten system lokacji w centralnej lokacji administracyjnej do synchronizacji z programem WSUS.  

    -   Skonfiguruj każde wystąpienie tej roli w podrzędnych lokacjach głównych do synchronizacji z witryny administracji centralnej.  

    -   W przypadku wolnego transferu danych za pośrednictwem sieci należy rozważyć zainstalowanie punktu aktualizacji oprogramowania w lokacjach dodatkowych.  

    Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

-   **Punkt migracji stanu.** Rola systemu lokacji, która przechowuje dane o stanie użytkownika podczas migrowania komputera do nowego systemu operacyjnego. Ta rola jest obsługiwana w lokacjach głównych i lokacjach dodatkowych. Można zainstalować wiele wystąpień tej roli w lokacji oraz w wielu lokacjach w tej samej hierarchii. Aby uzyskać więcej informacji o zapisywaniu stanu użytkownika podczas wdrażania systemu operacyjnego, zobacz [Zarządzanie stanem użytkownika w programie System Center Configuration Manager](../../../osd/get-started/manage-user-state.md).  

-   **Punkt modułu sprawdzania kondycji systemu.** Chociaż ta rola systemu lokacji jest widoczne w konsoli programu Configuration Manager, jest już używana.  

###  <a name="bkmk_proxy"></a> Role systemu lokacji, które mogą używać serwera proxy  
 Niektóre role systemu lokacji programu Configuration Manager wymagają połączenia z Internetem i korzystania z serwera proxy, jeśli serwer systemu lokacji, który jest hostem roli jest skonfigurowany do jednego. Zwykle to połączenie jest nawiązywane w **systemu** kontekstu komputer z zainstalowaną rolą systemu lokacji. Połączenie nie można używać konfiguracji serwera proxy dla typowych kont użytkowników. Jeżeli do nawiązania połączenia z Internetem wymagany jest serwer proxy, należy skonfigurować komputer do korzystania z serwera proxy:  

-   Można skonfigurować serwera proxy podczas instalowania roli systemu lokacji.  

-   Można dodać lub zmodyfikować konfigurację serwera proxy, korzystając z konsoli programu Configuration Manager.  

-   Taką samą konfigurację serwera proxy jest używany dla wszystkich ról systemu lokacji na serwerze systemu lokacji, które mogą używać konfiguracji serwera proxy. Jeśli potrzebujesz różne role systemu lokacji do używania różnych serwerów proxy, należy zainstalować role systemu lokacji na komputerach serwera systemu innej lokacji.  

-   W przypadku zmodyfikowania konfiguracji serwera proxy lub zainstalowania nowej roli systemu lokacji na komputerze dysponującym już konfiguracją serwera proxy oryginalna konfiguracja jest zastępowana nową.  


Procedury dotyczące konfigurowania serwera proxy dla ról systemu lokacji, zobacz [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/add-site-system-roles.md) tematu.  

Poniżej opisano role systemu lokacji, które mogą korzystać z serwera proxy:  

-   **Punkt synchronizacji analizy zasobów.** Ta rola systemu lokacji łączy do firmy Microsoft, korzysta z konfiguracji serwera proxy na komputerze, który obsługuje punkt synchronizacji analizy zasobów.  

-   **Punkt dystrybucji w chmurze.** Korzystając z punktu dystrybucji w chmurze, lokacji głównej zarządzającej punktem dystrybucji w chmurze musi być może nawiązać połączenia z programem Microsoft Azure do udostępnienia, monitorowania i dystrybucji zawartości do punktu dystrybucji. Jeśli dla tego połączenia wymagany jest serwer proxy, należy skonfigurować serwer proxy na serwerze lokacji głównej. Nie można skonfigurować serwera proxy w punkcie chmury dystrybucji w systemie Azure. Aby uzyskać więcej informacji, zobacz [skonfigurować ustawienia serwera proxy dla lokacji głównych zarządzających usługami w chmurze](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md#BKMK_ConfigProxyforCloud) w sekcji [zainstalować punkty dystrybucji w chmurze platformy Microsoft Azure dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md) tematu.  

-   **Łącznik serwera Exchange.** Ta rola systemu lokacji łączy się z serwerem Exchange i używa konfiguracji serwera proxy na komputerze, który obsługuje łącznik serwera Exchange.  

-   **Punkt aktualizacji oprogramowania.** Ta rola systemu lokacji może wymagać połączeń z usługą Microsoft Update w celu pobrania poprawek i synchronizowania informacji dotyczących aktualizacji. Zazwyczaj podczas konfigurowania serwera proxy każda rola systemu lokacji na danym komputerze obsługującym używanie serwera proxy używa serwera proxy. Dodatkowa konfiguracja nie jest wymagana. Wyjątkiem jest punkt aktualizacji oprogramowania. Domyślnie punkt aktualizacji oprogramowania nie używa dostępnego serwera proxy, chyba że włączono również następujące opcje podczas konfigurowania punktu aktualizacji oprogramowania:  

    -   **Użyj serwera proxy podczas synchronizowania aktualizacji oprogramowania**  

    -   **Do pobierania zawartości za pomocą reguł wdrażania automatycznego użyj serwera proxy**  

    > [!TIP]  
    >  Przed można wybrać jedną z opcji, serwer proxy należy skonfigurować na serwerze systemu lokacji, który jest hostem punktu aktualizacji oprogramowania. Serwer proxy jest używany tylko zgodnie z wybranymi opcjami.  

 Aby uzyskać więcej informacji o serwerach proxy punktów aktualizacji oprogramowania, zobacz sekcję "Ustawienia serwera Proxy" w [zainstalować punkt aktualizacji oprogramowania](../../../sum/get-started/install-a-software-update-point.md) tematu.  

-   **Punkt połączenia usługi.** Kiedy ustawić online (nie w trybie offline), ta rola systemu lokacji łączy się z Microsoft Intune i usługi w chmurze firmy Microsoft.  

