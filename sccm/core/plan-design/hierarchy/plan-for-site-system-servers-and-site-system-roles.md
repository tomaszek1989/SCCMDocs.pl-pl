---
title: "Planowanie ról systemu lokacji | Dokumentacja firmy Microsoft"
description: "Podczas planowania hierarchii programu System Center Configuration Manager, należy rozważyć serwery systemu lokacji i role systemu lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0a7415ba-2c53-4433-983e-780e92aa662f
caps.latest.revision: "11"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 0a3704a2d3b75ed7e0a7f718b681448ab6fc078d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-for-site-system-servers-and-site-system-roles-for-system-center-configuration-manager"></a>Planowanie serwerów i ról systemu lokacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Każda lokacja programu System Center Configuration Manager, należy zainstalować obejmuje serwer lokacji, który jest **serwera systemu lokacji**. Lokacja może obejmować także dodatkowe serwery systemu lokacji na komputerach zdalnych względem serwera lokacji. Serwery systemu lokacji (serwer lokacji lub zdalny serwer systemu lokacji) obsługują **role systemu lokacji**.


##  <a name="bkmk_siteservers"></a> Serwery systemu lokacji  
 Podczas instalowania roli systemu lokacji na komputerze komputer ten staje się serwerem systemu lokacji. W każdej lokacji można zainstalować jeden lub więcej dodatkowych serwerów systemu lokacji. Można także zainstalować dodatkowe serwery systemu lokacji i uruchamiać wszystkie role systemu lokacji bezpośrednio na komputerze serwera lokacji. Każdy serwer systemu lokacji obsługuje jedną lub więcej ról systemu lokacji. Dodatkowe serwery mogą pomóc rozszerzyć możliwości i wydajność lokacji za pomocą udostępniania obciążenie procesora CPU, że role systemu lokacji na serwerze.  

 Podczas rozważania dodania serwera systemu lokacji, upewnij się, że serwer spełnia wymagania wstępne związane z zamierzonym użyciem. Jest również dobrym rozwiązaniem, aby dodać go w lokalizacji sieciowej dysponującej przepustowością wystarczającą do komunikacji z oczekiwanymi punktami końcowymi, łącznie z serwera lokacji, domeny zasobów lokalizacji usługi opartej na chmurze, serwery systemu lokacji i klientów).  

 Jeśli skonfigurujesz serwer systemu lokacji z serwerem proxy do użytku przez role systemu lokacji, zobacz [lokacji role systemu, które mogą używać serwera proxy](#bkmk_proxy).  

##  <a name="bkmk_planroles"></a> Site system roles  
 Role systemu lokacji są instalowane na komputerze, aby zapewnić lokacji dodatkowe możliwości. Przykłady obejmują:  

-   Dodatkowe Zarządzanie punktów tak, aby lokacji może obsługiwać więcej urządzeń do witryny obsługiwana pojemność.  

-   Dodatkowych punktów dystrybucji aby rozwinąć infrastruktury zawartości poprawia wydajność dystrybucji zawartości do urządzeń i użytkowników.  

-   Jeden lub więcej ról systemu lokacji właściwych dla funkcji. Na przykład punkt aktualizacji oprogramowania umożliwia zarządzanie aktualizacjami oprogramowania dla zarządzanych urządzeń lub punkt usług raportowania pozwala uruchamiać raporty, aby monitorować i zrozumieć lub udostępniania informacji o wdrożeniu.  


Różne lokacje programu Configuration Manager może obsługiwać różne zestawy ról systemu lokacji. Zestaw obsługiwanych ról systemu lokacji zależy od typu lokacji (centralnej lokacji administracyjnej, lokacji głównej lub dodatkowej lokacji). Topologia hierarchii może ograniczać rozmieszczanie niektórych ról w określonych typów lokacji. Na przykład punkt połączenia usługi jest obsługiwany tylko w lokacji najwyższego poziomu w hierarchii, która może być centralną lokacją administracyjną lub autonomiczną lokacją główną. Ta rola nie jest obsługiwana w podrzędnej lokacji głównej ani w lokacjach dodatkowych.  

Po zainstalowaniu lokacji, należy przenieść lokalizację niektórych ról systemu lokacji z lokalizacji domyślnej na serwerze lokacji do innego serwera. Na przykład dotyczy to punkt zarządzania lub punktu dystrybucji, które są domyślnie instalowane na serwerze lokacji głównej lub dodatkowej. Można także zainstalować dodatkowe wystąpienia niektórych ról systemu lokacji, aby rozszerzyć możliwości lokacji (zapewnić więcej usług klientom) i w celu spełnienia wymagań biznesowych. Niektóre role są wymagane, a inne opcjonalne.  

-   **Serwer lokacji programu Configuration Manager.** Ta rola identyfikuje serwer, na którym uruchomiono Instalatora programu Configuration Manager do zainstalowania lokacji lub serwerze, na którym należy zainstalować lokacji pomocniczej. Tej roli nie można przenieść ani odinstalować do momentu odinstalowania lokacji.  

-   **System lokacji programu Configuration Manager.** Ta rola jest przypisywana do dowolnego komputera, na którym należy zainstalować lokację albo zainstalować rolę systemu lokacji. Tej roli nie można przenieść ani odinstalować do momentu usunięcia z komputera ostatniej roli systemu lokacji.  

-   **Rola systemu lokacji składnika programu Configuration Manager.** Ta rola identyfikuje system lokacji, który jest uruchamiane wystąpienie usługi głównej programu SMS, a jest wymagany do obsługi innych ról, takich jak punkty zarządzania. Tej roli nie można przenieść ani odinstalować do momentu usunięcia z komputera ostatniej stosownej roli systemu lokacji.  

-   **Serwer bazy danych lokacji programu Configuration Manager.** Ta rola jest przypisywana do serwerów systemu lokacji zawierających wystąpienie bazy danych lokacji dla lokacji. Ta rola tylko można przenieść do nowego serwera przez modyfikację lokacji do używania innego wystąpienia programu SQL Server do hostowania bazy danych lokacji.  

-   **Dostawca programu SMS.** Rola dostawcy programu SMS jest przypisywana do każdego komputera, który hostuje wystąpienie dostawcy programu SMS, interfejs pomiędzy konsolą programu Configuration Manager i bazy danych lokacji. Domyślnie ta rola jest instalowana automatycznie na serwerze lokacji centralnej lokacji administracyjnej i lokacji głównych. Można zainstalować dodatkowe wystąpienia w każdej lokacji w celu zapewnienia dostępu do dodatkowych użytkowników administracyjnych.  

     Aby zainstalować dodatkowych dostawców, należy uruchomić Instalatora programu Configuration Manager [zarządzania dostawcą programu SMS](../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider). Następnie możesz zainstalować dodatkowych dostawców na dodatkowych komputerach. Na komputerze można zainstalować tylko jedno wystąpienie dostawcy programu SMS, a komputer ten musi być w tej samej domenie co serwer lokacji.  

-   **Punkt usługi sieci web katalogu aplikacji.** Rola systemu lokacji, która dostarcza do witryny sieci Web katalogu aplikacji informacje o oprogramowaniu z biblioteki oprogramowania. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

-   **Punkt witryny sieci Web katalogu aplikacji.** Rola systemu lokacji, która dostarcza użytkownikom listę dostępnego oprogramowania z katalogu aplikacji. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

     Jeśli katalog aplikacji obsługuje komputery klienckie w Internecie, jest najlepszą praktyką zabezpieczeń zainstalować punkt witryny sieci Web katalogu aplikacji w sieci obwodowej, zabezpieczeń i zainstaluj punkt usługi sieci web katalogu aplikacji w sieci intranet.  

-   **Punkt synchronizacji analizy zasobów.** Rola systemu lokacji, która łączy się Microsoft w celu pobrania informacji o katalogu analizy zasobów. Ta rola przekazuje również nieskategoryzowanych tytułów, które mogą zostać uwzględnione w przyszłości w katalogu. Hierarchia obsługuje tylko jedno wystąpienie tej roli, a które musi znajdować się w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej). Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej, a następnie zainstalować ją w centralnej lokacji administracyjnej.   Aby uzyskać więcej informacji, zobacz [Analiza zasobów w programie System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Punkt rejestracji certyfikatu.** Rola systemu lokacji, która komunikuje się z serwerem, na którym działa usługa rejestracji urządzeń sieciowych. Ta rola zarządza żądaniami certyfikatów urządzeń używających prostego protokołu rejestrowania certyfikatów (SCEP). Ta rola jest obsługiwana tylko w lokacjach głównych i centralnej lokacji administracyjnej.

     Mimo że jeden punkt rejestracji certyfikatu może zapewniać funkcje całej hierarchii, można zainstalować wiele wystąpień tej roli w lokacji oraz w wielu lokacjach w tej samej hierarchii. Może to ułatwić równoważenia obciążenia. Jeśli w hierarchii istnieje wiele wystąpień, klienci są losowo przydzielani do jednego z punktów rejestracji certyfikatu.  

     Każdy punkt rejestracji certyfikatu wymaga dostępu do oddzielnego wystąpienia usługi rejestracji urządzeń sieciowych. Nie można skonfigurować, aby dwa lub więcej punktów rejestracji certyfikatu korzystało z tej samej usługi rejestracji urządzeń sieciowych. Ponadto punktu rejestracji certyfikatu nie można zainstalować na serwerze z uruchomioną usługą rejestracji urządzeń sieciowych.  

- **Punkt łącznika bramy zarządzania w chmurze.** Rola systemu lokacji do komunikowania się z [brama zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway).

-   **Punkt dystrybucji.** Rola systemu lokacji zawierająca pliki źródłowe do pobrania przez klientów, takie jak zawartość aplikacji, pakiety oprogramowania, aktualizacje oprogramowania, obrazy systemu operacyjnego i obrazy rozruchowe. Domyślnie ta rola jest instalowana na komputerze serwera lokacji nowych lokacji głównych i dodatkowych w momencie instalacji lokacji. Ta rola nie jest obsługiwana w witrynie Administracja centralna. Można zainstalować wiele wystąpień tej roli w obsługiwanej lokacji oraz w wielu lokacjach w tej samej hierarchii. Aby uzyskać więcej informacji, zobacz temat [Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) oraz [Zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   **Rezerwowy punkt stanu.** Rola systemu lokacji, która pomaga monitorować instalacje klienta i identyfikować klientów, które nie są zarządzane, ponieważ nie mogli komunikować się ze swoim punktem zarządzania. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji oraz w wielu lokacjach w tej samej hierarchii.     


-   **Punkt ochrony punktu końcowego.** Rola systemu lokacji, która korzysta z programu Configuration Manager do akceptowania postanowień licencyjnych programu Endpoint Protection i konfigurowania domyślnego członkostwa w usłudze ochrony chmury. Hierarchia obsługuje tylko jedno wystąpienie tej roli, a które musi znajdować się w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej). Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej, a następnie zainstalować ją w centralnej lokacji administracyjnej. Aby uzyskać więcej informacji, zobacz [programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

-   **Punkt rejestracji.** Rola systemu lokacji, która korzysta z certyfikatów PKI dla programu Configuration Manager do rejestracji urządzeń przenośnych i komputerów Mac. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

     Jeżeli użytkownik rejestruje urządzenia przenośne za pomocą programu Configuration Manager, a konto użytkownika usługi Active Directory znajduje się w niezaufanym lesie serwera lokacji, punkt rejestracyjny należy zainstalować w lesie użytkownika. Użytkownik mógł zostać uwierzytelniony.  

-   **Punkt proxy rejestracji.** Rola systemu lokacji, która zarządza żądaniami rejestrowania programu Configuration Manager z urządzeń przenośnych i komputerów Mac. Ta rola jest obsługiwana tylko w lokacjach głównych, ale można zainstalować wiele wystąpień tej roli w lokacji lub w wielu lokacjach w tej samej hierarchii.  

     W przypadku obsługi urządzeń przenośnych w Internecie, zainstalować punkt proxy rejestracji w sieci obwodowej zabezpieczeń i zainstalować punkt rejestracyjny w intranecie.  

-   **Łącznik serwera Exchange.** Aby uzyskać informacje o tej roli, zobacz [zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)  

-   **Punkt zarządzania.** Rola systemu lokacji, która dostarcza klientom informacji o lokalizacji zasad i usług oraz odbiera od klientów dane konfiguracji.  

    Domyślnie ta rola jest instalowana na komputerze serwera lokacji nowych lokacji głównych i dodatkowych w momencie instalacji lokacji. Lokacje główne obsługują wiele wystąpień tej roli. Lokacje dodatkowe obsługują pojedynczy punkt zarządzania, aby zapewnia lokalny punkt kontaktu dla klientów w celu uzyskania komputera i użytkownika zasady (punkt zarządzania w lokacji dodatkowej jest określone jako punkt zarządzania proxy).  

     Punkty zarządzania można skonfigurować do obsługi protokołu HTTP lub HTTPs, a także do obsługi urządzeń przenośnych, którymi można zarządzać z System Center Configuration Manager na — lokalne zarządzanie urządzeniami przenośnymi. Możliwe jest użycie [replik bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md), aby zmniejszyć obciążenie procesora CPU serwera bazy danych lokacji powodowanego przez punkty zarządzania obsługujące żądania od klientów.  

-   **Punkt usług raportowania.** Rola systemu lokacji, która integruje się z programem SQL Server Reporting Services do tworzenia i zarządzania raportami programu Configuration Manager. Ta rola jest obsługiwana w lokacjach głównych i centralnej lokacji administracyjnej, a można zainstalować wiele wystąpień tej roli w obsługiwanej lokacji. Aby uzyskać więcej informacji, zobacz [Planowanie raportowania w programie System Center Configuration Manager](../../../core/servers/manage/planning-for-reporting.md).  

-   **Punkt połączenia usługi.** Rola systemu lokacji, który umożliwia zarządzanie urządzeniami przenośnymi za pomocą Microsoft Intune i dla lokalnego zarządzania urządzeniami przenośnymi. Ta rola również przekazuje dane użycia z lokacji i jest wymagana do udostępnienia aktualizacji programu Configuration Manager dostępne w konsoli programu Configuration Manager. Hierarchia obsługuje tylko jedno wystąpienie tej roli, a które musi znajdować się w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej). Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej, a następnie zainstalować ją w centralnej lokacji administracyjnej. Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

-   **Punkt aktualizacji oprogramowania.** Rola systemu lokacji, która integruje się z systemu Windows Server Update Services (WSUS) w celu zapewniania aktualizacji oprogramowania dla klientów programu Configuration Manager. Ta rola jest obsługiwana we wszystkich lokacjach:  

    -   Zainstaluj ten system lokacji w centralnej lokacji administracyjnej do synchronizowania z serwerem WSUS.  

    -   Skonfiguruj każde wystąpienie tej roli w podrzędnych lokacjach głównych do synchronizacji z centralnej lokacji administracyjnej.  

    -   W przypadku wolnego transferu danych za pośrednictwem sieci należy rozważyć zainstalowanie punktu aktualizacji oprogramowania w lokacjach dodatkowych.  

    Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

-   **Punkt migracji stanu.** Rola systemu lokacji, która przechowuje dane o stanie użytkownika podczas migrowania komputera do nowego systemu operacyjnego. Ta rola jest obsługiwana w lokacjach głównych, jak i w lokacjach dodatkowych. Można zainstalować wiele wystąpień tej roli w lokacji i w wielu lokacjach w tej samej hierarchii. Aby uzyskać więcej informacji o zapisywaniu stanu użytkownika podczas wdrażania systemu operacyjnego, zobacz [Zarządzanie stanem użytkownika w programie System Center Configuration Manager](../../../osd/get-started/manage-user-state.md).  

-   **Punkt modułu sprawdzania kondycji systemu.** Mimo że ta rola systemu lokacji pozostaje widoczna w konsoli programu Configuration Manager, jest już używany.  

###  <a name="bkmk_proxy"></a> Role systemu lokacji, które mogą używać serwera proxy  
 Niektóre role systemu lokacji programu Configuration Manager wymagają połączenia z Internetem, a używany serwer proxy, jeśli serwer systemu lokacji, który jest hostem roli jest skonfigurowany do jednego. Zwykle to połączenie jest nawiązywane w **systemu** kontekstu komputera, na którym zainstalowano rolę systemu lokacji. Połączenie nie korzysta z konfiguracji serwera proxy dla typowych kont użytkowników. Gdy serwer proxy jest wymagany do nawiązania połączenia z Internetem, należy skonfigurować komputer do korzystania z serwera proxy:  

-   Można skonfigurować serwera proxy podczas instalowania roli systemu lokacji.  

-   Można dodać lub zmodyfikować konfigurację serwera proxy, korzystając z konsoli programu Configuration Manager.  

-   Tej samej konfiguracji serwera proxy jest używany dla wszystkich ról systemu lokacji na serwerze systemu lokacji, które mogą używać konfiguracji serwera proxy. Jeśli potrzebujesz różnych rolach systemu lokacji można używać różnych serwerów proxy, należy zainstalować role systemu lokacji na komputerach serwera systemu lokacji.  

-   W przypadku zmodyfikowania konfiguracji serwera proxy lub zainstalowania nowej roli systemu lokacji na komputerze dysponującym już konfiguracją serwera proxy oryginalna konfiguracja jest zastępowana nową.  


Procedury dotyczące konfigurowania serwera proxy dla ról systemu lokacji, zobacz [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/add-site-system-roles.md) tematu.  

Poniżej opisano role systemu lokacji, które mogą korzystać z serwera proxy:  

-   **Punkt synchronizacji analizy zasobów.** Ta rola systemu lokacji łączy do firmy Microsoft, używa konfiguracji serwera proxy na komputerze, który hostuje punkt synchronizacji analizy zasobów.  

-   **Punkt dystrybucji w chmurze.** Korzystając z punktu dystrybucji w chmurze, lokacji głównej zarządzającej punktem dystrybucji w chmurze musi być można nawiązać połączenia z programem Microsoft Azure w celu udostępniania, monitorowania i dystrybucji zawartości do punktu dystrybucji. Jeśli serwer proxy jest wymagane dla tego połączenia, należy skonfigurować serwer proxy na serwerze lokacji głównej. Nie można skonfigurować serwera proxy w chmurze na podstawie — punkt dystrybucji na platformie Azure. Aby uzyskać więcej informacji, zobacz [Skonfiguruj ustawienia serwera proxy dla lokacji głównych zarządzających usługami w chmurze](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md#BKMK_ConfigProxyforCloud) sekcji [zainstalować punkty dystrybucji w chmurze w systemie Microsoft Azure dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure.md) tematu.  

-   **Łącznik serwera Exchange.** Ta rola systemu lokacji łączy się z serwerem programu Exchange i używa konfiguracji serwera proxy na komputerze, który hostuje łącznik serwera Exchange.  

-   **Punkt aktualizacji oprogramowania.** Ta rola systemu lokacji może wymagać połączeń z witryną Microsoft Update, w celu pobrania poprawek i synchronizowania informacji dotyczących aktualizacji. Zazwyczaj podczas konfigurowania serwera proxy każda rola systemu lokacji na tym komputerze obsługującym używanie serwera proxy używa serwera proxy. Dodatkowa konfiguracja nie jest wymagane. Wyjątkiem jest punkt aktualizacji oprogramowania. Domyślnie punkt aktualizacji oprogramowania nie używa dostępnego serwera proxy, jeśli nie włączono również następujące opcje podczas konfigurowania punktu aktualizacji oprogramowania:  

    -   **Użyj serwera proxy podczas synchronizowania aktualizacji oprogramowania**  

    -   **Do pobierania zawartości za pomocą reguł wdrażania automatycznego użyj serwera proxy**  

    > [!TIP]  
    >  Zanim będzie można wybrać jedną z opcji, serwer proxy musi skonfigurować na serwerze systemu lokacji, który jest hostem punktu aktualizacji oprogramowania. Serwer proxy jest używany tylko zgodnie z wybranymi opcjami.  

 Aby uzyskać więcej informacji o serwerach proxy punktów aktualizacji oprogramowania, zobacz sekcję "Ustawienia serwera Proxy" w [instalacji punktu aktualizacji oprogramowania](../../../sum/get-started/install-a-software-update-point.md) tematu.  

-   **Punkt połączenia usługi.** Kiedy skonfigurować w trybie online (nie w trybie offline), ta rola systemu lokacji łączy się z Microsoft Intune i usługą w chmurze firmy Microsoft.  
