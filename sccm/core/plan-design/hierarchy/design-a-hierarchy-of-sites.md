---
title: Projektowanie hierarchii lokacji - Configuration Manager | Dokumentacja firmy Microsoft
description: "Poznać dostępne topologii i opcje zarządzania programu System Center Configuration Manager, można zaplanować hierarchię lokacji."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 07ce872e-1558-42ad-b5ad-582c5b1bdbb4
caps.latest.revision: 22
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 35e48666f4d1a2363304650f960531fd0630a291
ms.openlocfilehash: e346e83b0ae0dc7a612cef7a7b9fb1fdb42236bc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="design-a-hierarchy-of-sites-for-system-center-configuration-manager"></a>Projektowanie hierarchii lokacji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed zainstalowaniem pierwszej lokacji nowej hierarchii programu System Center Configuration Manager, to warto zrozumieć topologie dostępne dla programu Configuration Manager, typy dostępnych lokacji i ich relacji ze sobą i zakres zarządzania, który zapewnia typ każdej lokacji.
Następnie po uwzględnieniu opcji zarządzania zawartością, która pozwala zmniejszyć liczbę witryn, które należy zainstalować, można zaplanować topologia wydajnie pełniącą bieżącego potrzebami biznesowymi i później rozszerzyć do przyszłego rozwoju zarządzania.  

> [!NOTE]
> Podczas planowania nowej instalacji programu Configuration Manager, należy pamiętać o [informacje o wersji]( /sccm/core/servers/deploy/install/release-notes), które szczegółowo bieżących problemach w wersji aktywnych. Informacje o wersji dotyczą wszystkich gałęzi programu Configuration Manager.  Jednakże, gdy używasz [Technical Preview gałęzi]( /sccm/core/get-started/technical-preview), można znaleźć problemy specyficzne tylko dla tej gałęzi w dokumentacji dla każdej wersji Technical Preview.  

##  <a name="bkmk_topology"></a>Topologia hierarchii  
 Hierarchia topologie zakres od jednej autonomicznej lokacji głównej do grupy połączonych głównej i dodatkowej lokacji z centralnej lokacji administracyjnej w lokacji najwyższego poziomu (najwyższego poziomu) w hierarchii.   Sterownik klucza typu i liczby witryn korzystających w hierarchii jest zazwyczaj liczbę i typ urządzenia, które użytkownik musi obsługiwać, w następujący sposób:   

 **Autonomicznej lokacji głównej:** Użyj autonomicznej lokacji głównej podczas jednej lokacji głównej może obsługiwać zarządzania wszystkich urządzeń i użytkowników (zobacz [numery zmiany rozmiaru i skali](/sccm/core/plan-design/configs/size-and-scale-numbers)). Ta topologia również została wykonana pomyślnie, przy różnych miejscach w firmie można pomyślnie obsłużonych przez jednej lokacji głównej.  Aby ułatwić zarządzanie ruchu w sieci, można użyć preferowane punkty i dokładnie zaplanowany infrastruktury zawartości (zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md)).  

 Zalety tej topologii obejmują:  

-   Uproszczone koszty administracyjne.  

-   Uproszczone przypisania lokacji klienta i odnajdywanie dostępnych zasobów i usług.  

-   Eliminacja lag możliwe, wprowadzone przez replikację bazy danych między lokacjami.

-   Możliwość rozszerzenia autonomicznej hierarchii głównej do większej hierarchii z centralną lokacją administracyjną. Dzięki temu można następnie instalować nowe lokacje główne, aby rozszerzyć skalę wdrożenia.  


**Centralna lokacja administracyjna z jednego lub więcej podrzędnych lokacji głównych:** Ta topologia należy użyć, gdy potrzeba więcej niż jedną lokację główną do obsługi zarządzania urządzeniami i użytkownikami.  Jest wymagany, gdy trzeba użyć więcej niż jednej lokacji głównej. Zalety tej topologii obejmują:  


-   Obsługuje maksymalnie 25 lokacji głównych, które umożliwiają zwiększenie skali hierarchii.  

-   Zawsze będzie korzystać witryny administracji centralnej (bez ponownego zainstalowania lokacje). Jest to stały opcji. Nie można odłączyć podrzędnej lokacji głównej ma ona być autonomicznej lokacji głównej.

 Poniższe sekcje ułatwią zrozumienie, kiedy należy użyć określonej lokacji lub opcji zarządzania zawartością zamiast dodatkowej lokacji.  

##  <a name="BKMK_ChooseCAS"></a>Określa, kiedy użyj witryny Administracja centralna  
 Do konfigurowania ustawień całej hierarchii oraz monitorowania wszystkich lokacji i obiektów w hierarchii, należy użyć witryny Administracja centralna. Ten typ lokacji nie zarządza klientami bezpośrednio, ale koordynuje replikację danych między lokacjami, w tym konfiguracji lokacji i klientów w całej hierarchii.  

**Poniższe informacje ułatwiają zdecydować, kiedy mają być zainstalowane w witrynie Administracja centralna.**  

-   Witryna Administracja centralna jest lokacji najwyższego poziomu w hierarchii.  

-   Podczas konfigurowania hierarchii zawierającej więcej niż jednej lokacji głównej, należy zainstalować witryny administracji centralnej i musi być pierwszą instalowaną lokacją.  

-   Centralna lokacja administracyjna obsługuje tylko Lokacje główne jako Lokacje podrzędne.  

-   Witryna Administracja centralna nie może mieć przypisanych klientów.  

-   Centralna lokacja administracyjna nie obsługuje ról systemu lokacji, które bezpośrednio obsługują klientów, takich jak punkty zarządzania i punkty dystrybucji.  

-   Można zarządzać wszystkimi klientami w hierarchii i wykonywać zadania zarządzania lokacjami w ramach lokacji podrzędnych, korzystając z konsoli programu Configuration Manager, która jest połączona z lokacją administracji centralnej. Może to być instalowanie punktów zarządzania lub inne role systemu lokacji w lokacjach podrzędnych podstawowy lub pomocniczy.  

-   Gdy jest używana centralna lokacja administracyjna, tylko w tej lokacji można wyświetlać dane ze wszystkich lokacji w hierarchii. Te dane obejmują informacje takie jak magazynu danych i komunikaty o stanie.  

-   Można skonfigurować operacje odnajdywania w całej hierarchii z witryny administracji centralnej, przypisując metody odnajdywania uruchamianych w poszczególnych lokacjach.  

-   Zabezpieczeniami w hierarchii można zarządzać, przypisując różne role zabezpieczeń, zakresy zabezpieczeń i kolekcje do różnych użytkowników administracyjnych. Te konfiguracje mają zastosowanie w każdej lokacji w hierarchii.  

-   W ramach kontroli komunikacji między lokacjami w hierarchii istnieje możliwość skonfigurowania replikacji plików i bazy danych. Obejmuje to planowanie replikacji bazy danych lokacji i zarządzanie przepustowością transferu danych opartych na plikach między lokacjami.  

##  <a name="BKMK_ChoosePriimary"></a>Określa, kiedy używać lokacji podstawowej  
 Lokacje główne służą do zarządzania klientami. Lokację główną można zainstalować jako lokację podrzędną względem centralnej lokacji administracyjnej, a w przypadku nowej hierarchii — jako pierwszą lokację. Lokacja główna, która jest instalowany jako pierwszej lokacji hierarchii tworzy autonomicznej lokacji głównej. Zarówno podrzędne Lokacje główne, jak i autonomiczne Lokacje główne obsługują Lokacje dodatkowe jako Lokacje podrzędne względem lokacji głównej.  

 Użycie lokacji głównej zaleca się z następujących powodów:  

-   Do zarządzania urządzeniami i użytkownikami.  

-   Aby zwiększyć liczbę urządzeń, którymi można zarządzać z jednej hierarchii.  

-   Aby zapewnić dodatkowy punkt połączenia dla administracji wdrożenia.  

-   Umożliwia spełnienie wymagań organizacyjnych w zakresie zarządzania. Na przykład może zainstalować lokacji głównej w lokalizacji zdalnej, aby zarządzać transferem zawartości wdrożenia sieci o niskiej przepustowości. Jednakże za pomocą programu System Center Configuration Manager służy opcje ograniczania przepustowości sieci podczas przesyłania danych do punktu dystrybucji. Czy funkcja zarządzania zawartością może wyeliminować potrzebę instalowania dodatkowych lokacji.  


**Poniższe informacje mogą być pomocne w decydowaniu, podczas instalowania lokacji głównej:**  

-   Lokacja główna może być autonomicznej lokacji głównej lub podrzędnej lokacji głównej w dużej hierarchii. Jeżeli lokacja główna należy do hierarchii z centralną lokacją administracyjną, replikacja danych między lokacjami odbywa się w ramach replikacji bazy danych. W przypadku braku konieczności obsługi większej liczby klientów i urządzeń niż jednej lokacji głównej można zaleca się zainstalowanie autonomicznej lokacji głównej.  Po zainstalowaniu autonomicznej lokacji głównej można rozwinąć ją zgłosić do skalowania wdrożenia nowej witryny Administracja centralna.  

-   Lokacja główna obsługuje tylko witryny Administracja centralna jako lokację nadrzędną.  

-   Lokacja główna obsługuje tylko Lokacje dodatkowe jako Lokacje podrzędne i może także obsługiwać wiele lokacji dodatkowych.  

-   Lokacji głównych jest odpowiedzialna za przetwarzanie wszystkich danych z przypisanych im klientów.  

-   Przy użyciu replikacji bazy danych Lokacje główne do komunikowania się bezpośrednio do swojej witryny Administracja centralna, (która jest konfigurowana automatycznie podczas instalowania nowej lokacji).  

##  <a name="BKMK_ChooseSecondary"></a>Określa, kiedy używać lokacji dodatkowej  
 Lokacje dodatkowe służą do zarządzania transferem zawartości wdrożenia oraz klienta danymi w sieciach o niskiej przepustowości.  

 Lokację dodatkową zarządza się z centralnej lokacji administracyjnej lub lokacji dodatkowej bezpośrednie nadrzędnej lokacji głównej. Lokacje dodatkowe muszą być dołączone do lokacji głównej, a nie można przenieść je do innej lokacji nadrzędnej je odinstalować, a następnie zainstalować ponownie jako lokację podrzędną względem nowej lokacji głównej.

Jednak przesyłanie zawartości między dwoma równorzędnymi lokacjami dodatkowymi ułatwia zarządzanie replikacją zawartości wdrożenia opartą na plikach. Transferuje dane klienta do lokacji głównej, lokacja dodatkowa używa replikacji plikowej. Lokacja dodatkowa używa replikacji bazy danych również do komunikacji z jej nadrzędną lokacją główną.  

 Zaleca się zainstalowanie lokacji dodatkowej w przypadku spełnienia jednego z następujących warunków:  

-   Nie wymagasz lokalny punkt łączności dla użytkownika administracyjnego.  

-   Muszą zarządzać transferem zawartości wdrożenia do niższych lokacji w hierarchii.  

-   Informacje o kliencie, które są wysyłane do wyższych lokacji w hierarchii muszą zarządzać.  

 Aby uniknąć instalowania lokacji dodatkowej, gdy w lokalizacjach zdalnych znajdują się klienci, należy rozważyć użycie usługi Windows BranchCache lub instalację punktów dystrybucji z możliwością sterowania przepustowością i planowania. Można użyć tych opcji zarządzania zawartością, z użyciem lub bez Lokacje dodatkowe, a ich może ułatwić zmniejszenie liczby lokacji i serwerów, które należy zainstalować. Aby uzyskać informacje o opcjach zarządzania zawartością w programie Configuration Manager, zobacz [określić, kiedy należy używać opcji zarządzania zawartością](#BKMK_ChooseSecondaryorDP).  


**Następujące informacje mogą być pomocne w decydowaniu podczas instalacji lokacji dodatkowej:**  

-   Lokacje dodatkowe automatycznie instalują program SQL Server Express podczas instalacji lokacji Jeśli lokalne wystąpienie programu SQL Server nie jest dostępna.  

-   Instalacja lokacji dodatkowej jest inicjowana z konsoli programu Configuration Manager, a nie bezpośrednio na komputerze z systemem Instalatora.  

-   Lokacje dodatkowe za pomocą podzestawu informacji w bazie danych lokacji, co zmniejsza ilość danych replikacji bazy danych między nadrzędnej lokacji głównej i dodatkowej lokacji.  

-   Lokacje dodatkowe obsługują przesyłanie zawartości opartych na plikach do innych lokacji dodatkowych ze wspólną nadrzędną lokacją główną.  

-   Instalacji lokacji dodatkowych automatycznie są wdrażane punkt zarządzania i punkt dystrybucji, które znajdują się na serwerze lokacji dodatkowej.  

##  <a name="BKMK_ChooseSecondaryorDP"></a>Określa, kiedy używać opcji zarządzania zawartością  
 Jeżeli klienci znajdują się w zdalnych lokalizacjach sieciowych, zaleca się użycie co najmniej jednej opcji zarządzania zawartością zamiast lokacji głównej lub dodatkowej. Często może wyeliminować konieczność instalowania lokacji, gdy usługa Windows BranchCache, skonfiguruj punkty dystrybucji do kontroli przepustowości lub ręcznie skopiować zawartość do punktów dystrybucji (wstępnie przygotowana zawartość).  


**Zaleca się wdrożenie punktu dystrybucji zamiast instalowania innej lokacji w przypadku spełnienia jednego z następujących warunków:**  

-   Przepustowość sieci wystarcza komputerom klienckim w lokalizacjach zdalnych do komunikowania się z punktem zarządzania w celu pobierania zasad klienta oraz wysyłania informacji dotyczących zapasów, stanu raportowania i odnajdywania.  

-   Usługa inteligentnego transferu w tle (BITS) nie zapewnia odpowiedniej kontroli przepustowości, wymaganiach dotyczących sieci.  

 Aby uzyskać więcej informacji o opcjach zarządzania zawartością w programie Configuration Manager, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

##  <a name="bkmk_beyond"></a>Poza topologii hierarchii  
 Oprócz topologii początkowej hierarchii należy wziąć pod uwagę usług lub możliwości, które będą dostępne z różnych lokacji w hierarchii (Role systemu lokacji), a konfiguracje i możliwości jak całej hierarchii będą zarządzane w używanej infrastrukturze. Omówiono następujące zagadnienia dotyczące typowych w osobnych tematach. Są to ważne, ponieważ mogą mieć wpływ lub mieć wpływ na projekt hierarchii:  

-   Podczas przygotowywania do [zarządzania komputerami i urządzeniami z System Center Configuration Manager](/sccm/core/clients/manage/manage-clients), należy wziąć pod uwagę zarządzanych urządzeń lokalnych, w chmurze, czy zawiera urządzeń należących do użytkownika (BYOD).  Ponadto należy wziąć pod uwagę sposób zarządzania urządzeniami, które są obsługiwane przez wiele opcji zarządzania, takich jak komputery Windows 10, które mogą być zarządzane bezpośrednio przez program Configuration Manager lub że integracja z programem Microsoft Intune.  

-   Zrozumienie, jak dostępna infrastruktura sieci mogą mieć wpływ na przepływ danych między w lokalizacjach zdalnych (zobacz [przygotowanie środowiska sieciowego dla programu System Center Configuration Manager](/sccm/core/plan-design/network/configure-firewalls-ports-domains)). Należy również rozważyć, gdzie znajdują się geograficznie użytkowników i urządzeń, którymi można zarządzać, i czy infrastruktury im dostęp do Twojej domeny firmy lub w Internecie.  

-   Planowanie zawartości infrastruktury wydajnego rozpowszechniania informacji wdrażania (plików i aplikacji) urządzeniom zarządzasz (zobacz [Zarządzanie zawartości i infrastruktury dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md)).  

-   Określenie, które [funkcji i możliwości programu System Center Configuration Manager](../../../core/plan-design/changes/features-and-capabilities.md) planujesz używać, role systemu lokacji lub infrastruktury systemu Windows wymagają one i w których lokacjach w hierarchii wielu lokacji można je wdrożyć dla najbardziej efektywne wykorzystanie zasobów sieci i serwera.  

-   Należy rozważyć zabezpieczenia danych i urządzeń, w tym użycie infrastruktury kluczy publicznych. Zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  


**Przejrzyj następujące zasoby dotyczące konfiguracje specyficzne dla lokacji:**  

-   [Planowanie dostawcy programu SMS dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md)  

-   [Planowanie bazy danych lokacji programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-site-database.md)  

-   [Planowanie serwerów systemu lokacji i ról systemu lokacji dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md)  

-   [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md)  

-   [Zarządzanie przepustowością sieci](../../../core/plan-design/hierarchy/manage-network-bandwidth.md) podczas wdrażania zawartości w obrębie lokacji  


**Należy wziąć pod uwagę konfiguracji obejmującej Lokacje i hierarchie:**  

-   [Opcje wysokiej dostępności dla programu System Center Configuration Manager](/sccm/protect/understand/high-availability-options) dla lokacji i hierarchii

-   [Rozszerzenie schematu usługi Active Directory dla programu System Center Configuration Manager](../../../core/plan-design/network/extend-the-active-directory-schema.md) oraz konfigurowanie lokacji w celu [publikowania danych lokacji programu System Center Configuration Manager](../../../core/servers/deploy/configure/publish-site-data.md)  

-   [Transferu danych między lokacjami w programie System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md)  

-   [Podstawowe założenia administracji opartej na rolach dla programu System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md)

