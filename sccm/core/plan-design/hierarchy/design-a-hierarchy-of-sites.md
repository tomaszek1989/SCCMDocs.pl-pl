---
title: "Projektowanie hierarchii lokacji — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zrozumieć topologie dostępne i opcje zarządzania dla programu System Center Configuration Manager, co umożliwia planowanie hierarchii lokacji."
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
caps.latest.revision: "22"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 4710b1b89eb50cb7bcf4c4ee50c12a96b6561bc9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="design-a-hierarchy-of-sites-for-system-center-configuration-manager"></a>Projektowanie hierarchii lokacji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed rozpoczęciem instalacji pierwszej lokacji nowej hierarchii programu System Center Configuration Manager, to warto poznać topologie dostępne dla programu Configuration Manager, typy dostępnych lokacji i ich relacje ze sobą i zakresu zarządzania zapewnia każdego typu lokacji.
Następnie po uwzględnieniu opcji zarządzania zawartością, która pozwala zmniejszyć liczbę witryn, które należy zainstalować, można zaplanować topologii, wydajne pełniącą bieżącego potrzeb biznesowych i później rozszerzyć do zarządzania rozwój w przyszłości.  

> [!NOTE]
> Podczas planowania nowej instalacji programu Configuration Manager, należy pamiętać o [informacje o wersji]( /sccm/core/servers/deploy/install/release-notes), które szczegółowo bieżących problemach w aktywnych wersji. Informacje o wersji dotyczą wszystkie gałęzie programu Configuration Manager.  Jednak jeśli używasz [Technical Preview gałęzi]( /sccm/core/get-started/technical-preview), można znaleźć problemy specyficzne tylko dla tej gałęzi w dokumentacji dla każdej wersji Technical Preview.  

##  <a name="bkmk_topology"></a>Topologia hierarchii  
 Różne topologie hierarchii — od pojedynczej autonomicznej lokacji głównej do grupy połączonych lokacji głównych i dodatkowych z centralną lokacją administracyjną w lokacji najwyższego poziomu (w najwyższej warstwie) hierarchii.   Kluczowym czynnikiem decydującym o typie i liczbie lokacji używanych w hierarchii jest zwykle liczba i typ urządzeń, które należy obsługiwać, w następujący sposób:   

 **Autonomiczna lokacja główna:** Użyj autonomicznej lokacji głównej, gdy pojedyncza lokacja główna może obsługiwać zarządzanie wszystkimi urządzeniami i użytkownikami (zobacz [rozmiaru i skali liczby](/sccm/core/plan-design/configs/size-and-scale-numbers)). Ta topologia jest pomyślne również w przypadku, gdy w firmie różne lokalizacje geograficzne mogą być pomyślnie przekazywane przez jedną lokację główną.  Aby ułatwić zarządzanie ruchu sieciowego, można użyć preferowanych punktów zarządzania i dokładnie zaplanować infrastrukturę zawartości (zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)).  

 Zalety tej topologii obejmują:  

-   Uproszczony koszty administracyjne.  

-   Uproszczone przypisania lokacji klienta i wykrywanie dostępnych zasobów i usług.  

-   Eliminacja możliwe opóźnienia wprowadzone za pomocą replikacji bazy danych między lokacjami.

-   Opcję, aby rozszerzyć autonomiczną hierarchię główną do większej hierarchii z centralną lokacją administracyjną. Dzięki temu można następnie instalować nowe lokacje główne, aby rozszerzyć skalę wdrożenia.  


**Centralna lokacja administracyjna z co najmniej jedną podrzędną lokacją główną:** Jeśli wymagane jest więcej niż jedną lokację główną do obsługi zarządzania urządzeniami i użytkownikami za pomocą tej topologii.  Są wymagane, gdy konieczne jest użycie więcej niż jednej lokacji głównej. Zalety tej topologii obejmują:  


-   Obsługuje maksymalnie 25 lokacji głównych, które umożliwiają rozszerzyć skalę hierarchii.  

-   Centralna lokacja administracyjna będzie zawsze używana (bez ponownego zainstalowania lokacji). Jest to opcja trwałych. Nie można odłączyć podrzędnej lokacji głównej dokonanie autonomicznej lokacji głównej.

 Poniższe sekcje ułatwią zrozumienie, kiedy należy użyć określonej lokacji lub opcji zarządzania zawartością zamiast dodatkowej lokacji.  

##  <a name="BKMK_ChooseCAS"></a>Ustalanie, kiedy należy użyć witryny Administracja centralna  
 Do konfigurowania ustawień całej hierarchii oraz monitorowania wszystkich lokacji i obiektów w hierarchii, należy użyć witryny Administracja centralna. Ten typ lokacji nie bezpośrednie zarządzanie klientami, ale koordynuje replikację danych między lokacjami, w tym konfiguracji lokacji i klientów w całej hierarchii.  

**Poniższe informacje ułatwią podjęcie decyzji dotyczącej instalacji centralnej lokacji administracyjnej:**  

-   Centralna lokacja administracyjna jest lokacją najwyższego poziomu w hierarchii.  

-   Podczas konfigurowania hierarchii, która ma więcej niż jedną lokację główną, należy zainstalować centralną lokację administracyjną. Jeśli będziesz potrzebować co najmniej dwie lokacje główne bezpośrednio, najpierw zainstalować centralną lokację administracyjną. Gdy już istnieje lokacja główna i następnie zainstalować centralną lokację administracyjną, należy najpierw [rozszerzenia autonomicznej lokacji głównej](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand) do zainstalowania centralnej lokacji administracyjnej. 

-   Centralna lokacja administracyjna obsługuje tylko Lokacje główne jako Lokacje podrzędne.  

-   Centralna lokacja administracyjna nie może mieć przypisanych klientów.  

-   Centralna lokacja administracyjna nie obsługuje ról systemu lokacji, które obsługują bezpośrednio klientów, takie jak punkty zarządzania i punktów dystrybucji.  

-   Można zarządzać wszystkimi klientami w hierarchii i wykonywać zadania zarządzania lokacjami dla dowolnej lokacji podrzędnej, korzystając z konsoli programu Configuration Manager, która jest połączona z lokacją administracji centralnej. Może to obejmować instalowanie punktów zarządzania lub inne role systemu lokacji w lokacjach podrzędnych podstawowy lub pomocniczy.  

-   Gdy jest używana centralna lokacja administracyjna, tylko w tej lokacji można wyświetlać dane ze wszystkich lokacji w hierarchii. Te dane obejmują informacje takie jak magazynu danych i komunikatów o stanie.  

-   Można konfigurować operacje wykrywania w całej hierarchii z centralną lokacją administracyjną, przypisując metody odnajdywania poszczególnym lokacjom.  

-   Zabezpieczeniami w hierarchii można zarządzać, przypisując różne role zabezpieczeń, zakresy zabezpieczeń i kolekcje do różnych użytkowników administracyjnych. Te konfiguracje mają zastosowanie w każdej lokacji w hierarchii.  

-   W ramach kontroli komunikacji między lokacjami w hierarchii istnieje możliwość skonfigurowania replikacji plików i bazy danych. Obejmuje to planowanie replikacji bazy danych lokacji i zarządzanie przepustowością transferu danych opartych na plikach między lokacjami.  

##  <a name="BKMK_ChoosePriimary"></a>Ustalanie, kiedy należy używać lokacji głównej  
 Lokacje główne służą do zarządzania klientami. Lokację główną można zainstalować jako lokację podrzędną względem centralnej lokacji administracyjnej, a w przypadku nowej hierarchii — jako pierwszą lokację. Lokacji głównej, która jest zainstalowana jako pierwsza lokacja hierarchii tworzy autonomicznej lokacji głównej. Zarówno podrzędnych lokacji głównych, jak i autonomiczne Lokacje główne obsługują Lokacje dodatkowe jako Lokacje podrzędne względem lokacji głównej.  

 Użycie lokacji głównej zaleca się z następujących powodów:  

-   Do zarządzania urządzeniami i użytkownikami.  

-   Aby zwiększyć liczbę urządzeń, którymi można zarządzać w ramach jednej hierarchii.  

-   Aby zapewnić dodatkowy punkt łączności do administrowania wdrożeniem.  

-   Umożliwia spełnienie wymagań organizacyjnych w zakresie zarządzania. Na przykład może zainstalować lokacji głównej w lokalizacji zdalnej do zarządzania transferem zawartości wdrożenia w sieci o niskiej przepustowości. Jednak z programem System Center Configuration Manager służy opcje ograniczania przepustowości sieci używanej podczas transferu danych do punktu dystrybucji. Tej możliwości zarządzania zawartością można zastąpić potrzebę instalowania dodatkowych lokacji.  


**Poniższe informacje ułatwią podjęcie decyzji dotyczącej instalacji lokacji głównej:**  

-   Lokacja główna może być autonomicznej lokacji głównej lub podrzędnej lokacji głównej w dużej hierarchii. Jeżeli lokacja główna należy do hierarchii z centralną lokacją administracyjną, replikacja danych między lokacjami odbywa się w ramach replikacji bazy danych. Jeśli nie ma konieczności obsługi większej liczby klientów i urządzeń niż pojedyncza lokacja główna może obsługiwać, zaleca się zainstalowanie autonomicznej lokacji głównej.  Po zainstalowaniu autonomicznej lokacji głównej można ją rozszerzyć w zgłoszenia do nowej centralnej lokacji administracyjnej, aby skalować wdrożenie w górę.  

-   Lokacja główna obsługuje tylko centralną lokację administracyjną jako lokację nadrzędną.  

-   Lokacja główna obsługuje tylko Lokacje dodatkowe jako Lokacje podrzędne i może również obsługiwać wielu podrzędnych lokacji dodatkowych.  

-   Lokacje główne są odpowiedzialne za przetwarzanie wszystkich danych z przypisanych im klientów.  

-   Lokacje główne replikacji bazy danych do komunikowania się bezpośrednio z centralną lokacją administracyjną (która jest konfigurowana automatycznie podczas instalowania nowej lokacji).  

##  <a name="BKMK_ChooseSecondary"></a>Ustalanie, kiedy należy używać lokacji dodatkowej  
 Lokacje dodatkowe służą do zarządzania transferem zawartości wdrożenia oraz klienta danymi w sieciach o niskiej przepustowości.  

 Lokacją dodatkową zarządza się z centralnej lokacji administracyjnej lub lokacji głównej bezpośrednio nadrzędnej lokacji dodatkowej. Lokacje dodatkowe muszą być dołączone do lokacji głównej, a nie można przenieść je do innej lokacji nadrzędnej bez je odinstalować, a następnie zainstalować ponownie jako Lokacje podrzędne względem nowej lokacji głównej.

Jednak mogą przesyłać zawartość między dwiema równorzędnymi lokacjami dodatkowymi ułatwia zarządzanie replikacją zawartości wdrożenia opartą na plikach. Transferuje dane klienta do lokacji głównej, lokacja dodatkowa używa replikacji plikowej. Lokacja dodatkowa używa replikacji bazy danych również do komunikacji z jej nadrzędną lokacją główną.  

 Zaleca się zainstalowanie lokacji dodatkowej w przypadku spełnienia jednego z następujących warunków:  

-   Nie wymagają lokalny punkt łączności dla użytkownika administracyjnego.  

-   Należy zarządzać transferem zawartości wdrożenia do niższych lokacji w hierarchii.  

-   Informacje o kliencie, który jest wysyłany do wyższych lokacji w hierarchii należy zarządzać.  

 Aby uniknąć instalowania lokacji dodatkowej, gdy w lokalizacjach zdalnych znajdują się klienci, należy rozważyć użycie usługi Windows BranchCache lub instalację punktów dystrybucji z możliwością sterowania przepustowością i planowania. Możesz użyć tych opcji zarządzania zawartością z lub bez dodatkowej lokacji, a ich może pomóc zmniejszyć liczbę lokacji i serwerów, które należy zainstalować. Aby uzyskać informacje o opcjach zarządzania zawartością w programie Configuration Manager, zobacz [ustalanie, kiedy należy używać opcji zarządzania zawartością](#BKMK_ChooseSecondaryorDP).  


**Poniższe informacje ułatwią podjęcie decyzji dotyczącej instalacji lokacji dodatkowej:**  

-   Lokacje dodatkowe automatycznie instalują program SQL Server Express podczas instalacji lokacji Jeśli lokalne wystąpienie programu SQL Server nie jest dostępna.  

-   Instalacja lokacji dodatkowej jest inicjowana z konsoli programu Configuration Manager, zamiast uruchamiania Instalatora bezpośrednio na komputerze.  

-   Lokacje dodatkowe korzystają z podzbioru informacji w bazie danych lokacji, co zmniejsza ilość danych, które są replikowane w ramach replikacji bazy danych między nadrzędnej lokacji głównej i dodatkowej lokacji.  

-   Lokacje dodatkowe obsługują przesyłanie zawartości opartej na plikach do innych lokacji dodatkowych ze wspólną nadrzędną lokacją główną.  

-   Instalacja lokacji dodatkowej powoduje automatyczne wdrażanie punkt zarządzania i punkt dystrybucji, które znajdują się na serwerze lokacji dodatkowej.  

##  <a name="BKMK_ChooseSecondaryorDP"></a>Ustalanie, kiedy należy używać opcji zarządzania zawartością  
 Jeżeli klienci znajdują się w zdalnych lokalizacjach sieciowych, zaleca się użycie co najmniej jednej opcji zarządzania zawartością zamiast lokacji głównej lub dodatkowej. Często można usunąć konieczności instalowania lokacji, gdy usługa Windows BranchCache, konfigurując punkty dystrybucji do kontroli przepustowości lub ręcznie skopiuj zawartość do punktów dystrybucji (wstępne przygotowywanie zawartości).  


**Należy rozważyć wdrożenie punktu dystrybucji zamiast instalowania innej lokacji w przypadku spełnienia jednego z następujących warunków:**  

-   Przepustowość sieci wystarcza komputerom klienckim w lokalizacjach zdalnych do komunikowania się z punktem zarządzania w celu pobrania zasad klienta oraz wysyłania spisu, stanu raportowania i informacji dotyczących odnajdywania.  

-   Usługa inteligentnego transferu w tle (BITS) nie zapewnia odpowiedniej kontroli przepustowości do wymagań sieci.  

 Aby uzyskać więcej informacji o opcjach zarządzania zawartością w programie Configuration Manager, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

##  <a name="bkmk_beyond"></a>Poza topologia hierarchii  
 Oprócz topologii początkowej hierarchii należy wziąć pod uwagę usług lub możliwości, które będą dostępne w różnych lokacjach w hierarchii (Role systemu lokacji) i konfiguracji i możliwości jak całej hierarchii, będą zarządzane w infrastrukturze. W osobnych tematach opisano następujące typowe kwestie wymagające rozważenia. Są to ważne, ponieważ mogą mieć wpływ lub mieć wpływ na projekt hierarchii:  

-   Podczas przygotowywania [zarządzania komputerami i urządzeniami w programie System Center Configuration Manager](/sccm/core/clients/manage/manage-clients), należy wziąć pod uwagę zarządzanych urządzeń lokalnych, w chmurze, czy obejmują urządzenia należące do użytkowników (BYOD).  Ponadto należy wziąć pod uwagę sposób będą zarządzać urządzeniami, które są obsługiwane przez wiele opcji zarządzania, takich jak komputery z systemem Windows 10, które mogą być zarządzane bezpośrednio przez program Configuration Manager lub że integracja z usługą Microsoft Intune.  

-   Zrozumienie, jak dostępna infrastruktura sieci może wpływać na przepływ danych między lokacjami zdalnymi (zobacz [przygotowanie środowiska sieciowego dla programu System Center Configuration Manager](/sccm/core/plan-design/network/configure-firewalls-ports-domains)). Należy również rozważyć, gdzie znajdują się geograficznie użytkowników i urządzeń, którymi zarządzasz, i czy uzyskują oni dostęp do infrastruktury za pośrednictwem domeny firmowej lub Internetu.  

-   Plan infrastruktury zawartości umożliwiająca efektywną dystrybucję informacje, Wdróż (plików i aplikacji) do urządzeń zarządzanych (zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)).  

-   Określenie, które [funkcje i możliwości programu System Center Configuration Manager](../../../core/plan-design/changes/features-and-capabilities.md) planujesz użyć, infrastruktury systemu Windows lub role systemu lokacji wymagają i w których lokacjach w hierarchii wielu lokacji może wdrożyć je dla najbardziej efektywne wykorzystanie zasobów sieci i serwera.  

-   Należy rozważyć zabezpieczenia danych i urządzeń, w tym użycie infrastruktury kluczy publicznych. Zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  


**Przejrzyj poniższe zasoby konfiguracje specyficzne dla lokacji:**  

-   [Planowanie dostawcy programu SMS dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)  

-   [Planowanie bazy danych lokacji programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-site-database.md)  

-   [Planowanie serwerów systemu lokacji i ról systemu lokacji dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)  

-   [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md)  

-   [Zarządzanie przepustowością sieci](../../../core/plan-design/hierarchy/manage-network-bandwidth.md) podczas wdrażania zawartości w obrębie lokacji  


**Należy wziąć pod uwagę konfiguracje obejmujące Lokacje i hierarchie:**  

-   [Opcje wysokiej dostępności dla programu System Center Configuration Manager](/sccm/protect/understand/high-availability-options) dla lokacji i hierarchii

-   [Rozszerzenie schematu usługi Active Directory dla programu System Center Configuration Manager](../../../core/plan-design/network/extend-the-active-directory-schema.md) oraz konfigurowanie lokacji do [publikowania danych lokacji programu System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md)  

-   [Transfer danych między lokacjami w programie System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md)  

-   [Podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md)
