---
title: Przygotowanie do zainstalowania lokacji | Dokumentacja firmy Microsoft
description: "Jeśli planujesz zainstalować wiele lokacji programu Configuration Manager, przeczytaj te informacje, aby zaoszczędzić czas i aby zapobiec wystąpieniu błędów."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9089e1b5-cba4-42bd-a2de-126ef882a3af
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 829f2d44a9b8d203a5b753ebb6d8f759b1a05111
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-to-install-system-center-configuration-manager-sites"></a>Przygotowanie do instalacji lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby przygotować się do pomyślnego wdrożenia co najmniej jednej lokacji programu System Center Configuration Manager, poznać szczegółowe informacje w tym artykule. Te kroki można zaoszczędzić czas podczas instalacji wielu witryn i zapobiec missteps, które może spowodować konieczność ponownej instalacji co najmniej jednej lokacji.

> [!TIP]
> Podczas zarządzania w lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* służą do opisywania trzy oddzielne pojęcia. Aby dowiedzieć się, jak każdego terminu jest używany, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).

## <a name="bkmk_options"></a>Opcje instalacji różnych typów lokacji
Podczas instalowania nowej lokacji programu Configuration Manager wersji plików źródłowych, których można użyć zależy od wersji witryn, które już znajdują się w hierarchii (jeśli istnieje). Metody instalacji, których można użyć, zależą od typu lokacji, którą chcesz zainstalować.  

Przed zainstalowaniem lokacji, upewnij się, zaplanowano hierarchii, oraz że znasz typ lokacji, którą chcesz zainstalować. Aby uzyskać więcej informacji, zobacz [Projektowanie hierarchii lokacji](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).


### <a name="first-site"></a>Pierwsza lokacja
Pierwsza lokacja instalowana w hierarchii będzie autonomicznej lokacji głównej lub centralnej lokacji administracyjnej.

**Nośnik instalacyjny**: Aby zainstalować centralną lokację administracyjną lub autonomiczną lokację główną jako pierwszą lokację w nowej hierarchii, należy najpierw [użyć wersji bazowej](../../../../core/servers/manage/updates.md#bkmk_Baselines) programu Configuration Manager. Nie należy instalować pierwszej lokacji nowej hierarchii przy użyciu zaktualizowanych plików źródłowych z [dysku CD. Najnowszy folder](../../../../core/servers/manage/the-cd.latest-folder.md) dowolnej lokacji.

**Metoda instalacji**: Dowolnego typu lokacji można zainstalować za pomocą [Kreatora instalacji programu Configuration Manager](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md), lub można skonfigurować za pomocą skryptu [pisanie skryptów wiersza polecenia instalacji](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).


### <a name="additional-sites"></a>Dodatkowe witryny
Po początkowej lokacji jest zainstalowana, można dodać więcej witryn w dowolnym momencie. Masz następujące opcje dodawania witryny (do [obsługiwane limity](../../../../core/plan-design/configs/size-and-scale-numbers.md)):

|Miejsca|Typ lokacji dodatkowych, które można zainstalować|
|---|---|
|Centralna lokacja administracyjna|Podrzędna lokacja główna|
|Podrzędna lokacja główna|Lokacja dodatkowa|
|Autonomiczna lokacja główna|Lokacja dodatkowa (można rozszerzyć lokacji głównej, który konwertuje autonomiczną lokację główną podrzędną lokacją główną)|

**Nośnik instalacyjny**: Podczas instalowania centralnej lokacji administracyjnej w celu rozszerzenia autonomicznej lokacji głównej lub instalowania nowej podrzędnej lokacji głównej w istniejącej hierarchii, należy użyć nośnika instalacyjnego, (który zawiera pliki źródłowe), które odpowiadają wersji istniejącej lokacji lub lokacji.

> [!IMPORTANT]
> Po zainstalowaniu aktualizacji w konsoli, które zmieniły wersję zainstalowanych wcześniej lokacji, nie należy używać oryginalnego nośnika instalacyjnego. W tym scenariuszu, użyj plików źródłowych z [dysku CD. Najnowszy folder](../../../../core/servers/manage/the-cd.latest-folder.md) zaktualizowane witryny. Configuration Manager wymaga użycia plików źródłowych odpowiadających wersji istniejącej lokacji, które będą się łączyć nowej witryny.

Lokację dodatkową należy zainstalować z konsoli programu Configuration Manager. W ten sposób Lokacje dodatkowe zawsze są instalowane za pomocą plików źródłowych z nadrzędnej lokacji głównej.

**Metoda instalacji**: Metodę, która służy do instalowania dodatkowych lokacji zależy od typu lokacji, którą chcesz zainstalować.
-   **Dodawanie centralnej lokacji administracyjnej**:  Aby zainstalować nową centralną lokację administracyjną jako lokację nadrzędną istniejącej autonomicznej lokacji głównej można użyć Kreatora instalacji programu Configuration Manager lub przy użyciu skryptu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [rozszerzania autonomicznej lokacji głównej](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand).
-   **Dodaj podrzędnej lokacji głównej**:  Aby dodać lokację główną podrzędną poniżej centralnej lokacji administracyjnej można użyć Kreatora instalacji programu Configuration Manager lub wiersza polecenia instalacji.
-   **Dodawanie lokacji dodatkowej**:  Użyj konsoli programu Configuration Manager, aby zainstalować lokację dodatkową jako lokację podrzędną lokację główną. Inne metody dodawania Lokacje dodatkowe są nieobsługiwane.

## <a name="bkmk_tasks"></a>Typowe zadania do wykonania przed rozpoczęciem instalacji
-   **Zrozumienie topologia hierarchii, które będą używane dla danego wdrożenia**    
Aby uzyskać więcej informacji, zobacz [Projektowanie hierarchii lokacji programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

-   **Przygotowanie i skonfigurować poszczególne serwery w celu spełnienia wymagań wstępnych i obsługiwanych konfiguracji do użycia z programem Configuration Manager**         
Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  

-   **Instalowanie i konfigurowanie programu SQL Server do hostowania bazy danych lokacji**     
Aby uzyskać więcej informacji, zobacz [pomocy technicznej dla wersji programu SQL Server dla programu System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   **Przygotowanie środowiska sieciowego do obsługi programu Configuration Manager**      
Aby uzyskać więcej informacji, zobacz [Konfigurowanie zapór, portów i domen, aby przygotować dla programu Configuration Manager](../../../../core/plan-design/network/configure-firewalls-ports-domains.md).  

- **Jeśli korzystasz z infrastruktury kluczy publicznych (PKI), przygotowanie infrastruktury i certyfikatów**      
Aby uzyskać więcej informacji, zobacz [wymagania dotyczące certyfikatu PKI dla programu Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).

-   **Zainstaluj najnowsze aktualizacje zabezpieczeń na komputerach, które będzie używane jako serwery lokacji lub serwery systemu lokacji i w razie potrzeby uruchomić je ponownie**

## <a name="bkmk_sitecodes"></a>O nazwach lokacji i kodach lokacji
Kody i nazwy lokacji służą do identyfikowania i zarządzania lokacji w hierarchii programu Configuration Manager. W konsoli programu Configuration Manager kod lokacji i nazwa lokacji są wyświetlane w &lt; *kod lokacji*\> - &lt;*nazwa witryny* \> format. Każdy kod lokacji używany w hierarchii musi być unikatowa. Jeśli schemat usługi Active Directory zostanie rozszerzony dla programu Configuration Manager, a lokacje publikują dane, kody lokacji w lesie usługi Active Directory musi być unikatowa, nawet jeśli są używane w innej hierarchii programu Configuration Manager lub jeśli były używane w przypadku wcześniejszej instalacji programu Configuration Manager. Należy dokładnie zaplanować kody i nazwy lokacji przed wdrożeniem hierarchii.

### <a name="specify-a-site-code-and-site-name"></a>Określ kod lokacji i nazwa lokacji
Po uruchomieniu Instalatora programu Configuration Manager, wyświetlany jest monit o kod i nazwę lokacji centralnej lokacji administracyjnej, a dla każdej lokacji głównej i instalacji lokacji dodatkowej. Kod lokacji musi unikatowo identyfikować każdej lokacji w hierarchii. Ponieważ kody lokacji są używane w nazwach folderów, nigdy nie używaj następujących nazw dla kodu lokacji, obejmujących nazwy zarezerwowane dla programu Configuration Manager i systemu Windows:
  -  AUX
  -  KON
  -  NUL
  -  PRN
  -  SMS

> [!NOTE]
> Instalator programu Configuration Manager nie sprawdza, czy kod lokacji nie jest już używany.

Aby wprowadzić kod lokacji dla lokacji, po uruchomieniu Instalatora programu Configuration Manager, należy wprowadzić trzy znaki alfanumeryczne. Tylko litery *A* za pośrednictwem *Z* i numery *0* za pośrednictwem *9*, w dowolnej kombinacji są dozwolone w kody lokacji. Sekwencja liter i cyfr nie ma wpływu na komunikacji między lokacjami. Na przykład nie jest konieczne nazwanie lokacji głównej *ABC* a lokacją dodatkową *DEF*.

Nazwa lokacji jest identyfikatorem przyjazną nazwę witryny. Można używać tylko znaków *A* za pośrednictwem *Z*, ** za pośrednictwem *z*, *0* za pośrednictwem *9*oraz znaki łącznika (*-*) w nazwach lokacji.

> [!IMPORTANT]
> Zmiana nazwy lokacji po zainstalowaniu lokacji lub kod lokacji nie jest obsługiwane.

### <a name="reuse-a-site-code"></a>Ponowne użycie kodu lokacji
Kody lokacji nie można użyć więcej niż jeden raz w hierarchii programu Configuration Manager dla centralnej lokacji administracyjnej lub lokacji głównej, nawet jeśli oryginalnej witryny i kod lokacji został odinstalowany. Ponowne użycie kodu lokacji, istnieje ryzyko konfliktem ID obiektów w hierarchii. Jeśli w tej lokacji dodatkowej i kod lokacji nie są już używane w hierarchii programu Configuration Manager lub w lesie usługi Active Directory, można użyć ponownie kod lokacji dla lokacji dodatkowej.

## <a name="limits-and-restrictions-for-installed-sites"></a>Ograniczenia dotyczące zainstalowanych lokacji
Przed zainstalowaniem lokacji należy koniecznie pamiętać o następujących ograniczeniach, które są stosowane do lokacji i hierarchii w lokacji:
-   Po zakończeniu instalacji, nie można zmienić następujących właściwości lokacji bez odinstalowania lokacji i zainstalować go ponownie przy użyciu nowych wartości:  
  -   Katalog instalacyjny plików programu  
  -   Kod lokacji  
  -   Opis lokacji  
-   Jeśli hierarchia obejmuje centralną lokację administracyjną:  
  -   Menedżer konfiguracji nie obsługuje przenoszenia podrzędnej lokacji głównej poza hierarchię w celu utworzenia autonomicznej lokacji głównej lub dołączenie go do innej hierarchii. Zamiast tego należy odinstalować podrzędną lokację główną, a następnie zainstalować ją ponownie jako nową autonomiczną lokację główną lub lokacją podrzędną lokacji centralnej lokacji administracyjnej z innej hierarchii.  


## <a name="bkmk_optionalsteps"></a>Opcjonalne kroki przed uruchomieniem Instalatora
**Ręcznie uruchom [Narzędzie pobierania Instalatora](../../../../core/servers/deploy/install/setup-downloader.md)**

Aby pobrać zaktualizowane pliki Instalatora programu Configuration Manager, możesz uruchomić Narzędzie pobierania Instalatora. Jeśli komputer, na którym zostanie uruchomiony Instalator nie jest połączony z Internetem lub jeśli będziesz instalować wiele serwerów lokacji, należy wziąć pod uwagę przy użyciu narzędzia pobierania Instalatora, aby pobrać aktualizacje do zainstalowania. Poniżej przedstawiono dodatkowe informacje:
-  Domyślnie Instalator łączy się z Internetem, aby pobrać zaktualizowane pliki Instalatora.
-  Domyślnie pliki są przechowywane w folderze Redist.
-  Można wskazać Instalatorowi lokalizację w sieci, w której uprzednio zapisano kopię tych plików.

**Ręcznie uruchom [narzędzie sprawdzania wymagań wstępnych](../../../../core/servers/deploy/install/prerequisite-checker.md)**

Aby zidentyfikować i rozwiązać problemy, przed uruchomieniem Instalatora w celu zainstalowania lokacji oraz przed zainstalowaniem roli systemu lokacji na serwerze, należy uruchomić narzędzie sprawdzania wymagań wstępnych. Narzędzie sprawdzania wymagań wstępnych pomaga, upewnij się, że komputer spełnia wymagania dotyczące hostowania lokacji lub rola systemu lokacji. Poniżej przedstawiono dodatkowe informacje:
 -  Domyślnie Instalator uruchamia narzędzie sprawdzania wymagań wstępnych.
 -  Jeśli wystąpią jakieś błędy, Instalator zatrzymuje, dopóki ten problem zostanie rozwiązany.

**Określ opcjonalne porty**

Można określić opcjonalne porty dla systemów lokacji i klientów do użycia. Poniżej przedstawiono dodatkowe informacje:
 -  Systemy lokacji i klientów domyślnie używa wstępnie zdefiniowanych portów do komunikacji.
 -  Podczas instalacji można skonfigurować alternatywne porty.

 Aby uzyskać więcej informacji, zobacz [porty używane w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/ports.md).
