---
title: Przygotowanie do zainstalowania lokacji | Dokumentacja firmy Microsoft
description: "Jeśli planujesz zainstalowanie wielu lokacji programu Configuration Manager, przeczytaj te informacje, aby pomóc Ci zaoszczędzić czas i aby zapobiec wystąpieniu błędów."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9089e1b5-cba4-42bd-a2de-126ef882a3af
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 73c34d40d70fb3ae5f8702f3d5f1e5b51a1b28a7
ms.openlocfilehash: 829f2d44a9b8d203a5b753ebb6d8f759b1a05111
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="prepare-to-install-system-center-configuration-manager-sites"></a>Przygotowanie do instalacji lokacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aby przygotować się na pomyślne wdrożenie co najmniej jednej lokacji programu System Center Configuration Manager, poznać szczegółowe informacje w tym artykule. Te kroki można zaoszczędzić czas podczas instalacji wielu lokacji i zapobiec missteps, które może powodować konieczność ponownej instalacji co najmniej jednej lokacji.

> [!TIP]
> Podczas zarządzania lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* są używane do opisywania trzy oddzielne pojęcia. Aby dowiedzieć się, jak używać każdego terminu, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).

## <a name="bkmk_options"></a>Opcje instalacji różnych typach witryn
Po zainstalowaniu nowej lokacji programu Configuration Manager wersji plików źródłowych, których można użyć zależy od wersji lokacji, które znajdują się już w hierarchii (jeśli istnieje). Metody instalacji, których można użyć zależą od typu obiektu, który chcesz zainstalować.  

Przed zainstalowaniem lokacji, upewnij się, zaplanowano hierarchii i sprawdź typ obiektu, który chcesz zainstalować. Aby uzyskać więcej informacji, zobacz [projektowania hierarchii lokacji](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).


### <a name="first-site"></a>Pierwszej lokacji
Pierwszy instalowanej w hierarchii lokacji będzie autonomicznej lokacji głównej lub centralnej lokacji administracyjnej.

**Nośnik instalacyjny**: Aby zainstalować centralnej lokacji administracyjnej lub autonomicznej lokacji głównej jako pierwszą lokację w nowej hierarchii, należy najpierw [wersji linii bazowej](../../../../core/servers/manage/updates.md#bkmk_Baselines) programu Configuration Manager. Nie należy instalować pierwszej lokacji nowej hierarchii za pomocą plików źródłowych zaktualizowane z [dysku CD. Najnowszy folder](../../../../core/servers/manage/the-cd.latest-folder.md) z dowolnej lokacji.

**Metoda instalacji**: Każdy typ lokacji można zainstalować za pomocą [Kreatora instalacji programu Configuration Manager](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md), lub można skonfigurować za pomocą skryptu [inicjowanych przez skrypty wiersza polecenia instalacji](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).


### <a name="additional-sites"></a>Lokacje dodatkowe
Po początkowej lokacji jest zainstalowany, należy dodać więcej lokacji w dowolnym momencie. Masz następujące opcje dodawania witryn (maksymalnie [obsługiwane limity](../../../../core/plan-design/configs/size-and-scale-numbers.md)):

|Miejsca|Typ lokacji dodatkowych, które można zainstalować|
|---|---|
|Centralna lokacja administracyjna|Podrzędna lokacja główna|
|Podrzędna lokacja główna|Lokacja dodatkowa|
|Autonomiczna lokacja główna|(Można rozszerzyć lokacji głównej, który konwertuje autonomicznej lokacji głównej podrzędnej lokacji głównej) lokacji dodatkowej|

**Nośnik instalacyjny**: Podczas instalowania centralnej lokacji administracyjnej rozszerzenia autonomicznej lokacji głównej lub po zainstalowaniu nowej lokacji głównej podrzędnych w istniejącej hierarchii, należy użyć nośnika instalacyjnego, (zawierającego pliki źródłowe), który odpowiada wersji istniejącej lokacji lub lokacji.

> [!IMPORTANT]
> Po zainstalowaniu aktualizacji w konsoli, które zostały zmienione w wersji uprzednio zainstalowanej lokacji, nie należy używać oryginalnego nośnika instalacyjnego. W tym scenariuszu, użyj plików źródłowych z [dysku CD. Najnowszy folder](../../../../core/servers/manage/the-cd.latest-folder.md) zaktualizowanej witryny. Program Configuration Manager wymaga użycia pliki źródłowe, które pasują do wersji istniejącej lokacji, który nowej witryny będzie łączyć się.

Musi być zainstalowany lokacji dodatkowej z konsoli programu Configuration Manager. W ten sposób Lokacje dodatkowe są zawsze instalowane za pomocą plików źródłowych z nadrzędnej lokacji głównej.

**Metoda instalacji**: Metody używane do instalowania dodatkowych lokacji zależy od typu obiektu, który chcesz zainstalować.
-   **Dodaj witryny Administracja centralna**:  Można użyć Kreatora instalacji programu Configuration Manager lub przy użyciu skryptu wiersza polecenia do zainstalowania nowej centralnej lokacji administracyjnej jako lokację nadrzędną istniejącej autonomicznej lokacji głównej. Aby uzyskać więcej informacji, zobacz [rozszerzania autonomicznej lokacji głównej](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand).
-   **Dodaj podrzędna lokacja główna**:  Instalację z wiersza polecenia lub Kreatora instalacji programu Configuration Manager umożliwia dodawanie podrzędnej lokacji głównej w witrynie Administracja centralna.
-   **Dodawanie lokacji dodatkowej**:  Konsoli programu Configuration Manager należy zainstalować lokacji dodatkowej jako lokacji podrzędnej lokacji głównej. Inne metody dodawania Lokacje dodatkowe są nieobsługiwane.

## <a name="bkmk_tasks"></a>Typowe zadania do wykonania przed rozpoczęciem instalacji
-   **Zrozumienie topologii hierarchii, który będzie używany dla danego wdrożenia**    
Aby uzyskać więcej informacji, zobacz [projektowania hierarchii lokacji programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md).  

-   **Przygotowania i skonfigurowania poszczególnych serwerów w celu spełnienia wymagań wstępnych i obsługiwanych konfiguracji do użycia z programu Configuration Manager**         
Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  

-   **Instalowanie i konfigurowanie programu SQL Server do obsługi bazy danych lokacji**     
Aby uzyskać więcej informacji, zobacz [obsługę wersji programu SQL Server dla programu System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   **Przygotowanie środowiska sieciowego do obsługi programu Configuration Manager**      
Aby uzyskać więcej informacji, zobacz [Konfigurowanie zapór, portów i domen, aby przygotować dla programu Configuration Manager](../../../../core/plan-design/network/configure-firewalls-ports-domains.md).  

- **Jeśli skorzystasz z infrastruktury kluczy publicznych (PKI), przygotuj skonfigurowaniu infrastruktury oraz certyfikatów**      
Aby uzyskać więcej informacji, zobacz [wymagania dotyczące certyfikatu PKI dla programu Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).

-   **Zainstaluj najnowsze aktualizacje zabezpieczeń na komputerach, które będzie używane jako serwery lokacji lub serwerach systemu lokacji i w razie potrzeby uruchomić je ponownie**

## <a name="bkmk_sitecodes"></a>O kody lokacji i nazwy lokacji
Kody i nazwy lokacji służą do identyfikowania i zarządzania lokacji w hierarchii programu Configuration Manager. W konsoli programu Configuration Manager kod i nazwę lokacji są wyświetlane w &lt; *kod lokacji*\> - &lt;*Nazwa lokacji* \> format. Każdy kod lokacji używany w hierarchii musi być unikatowa. Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager, a lokacje publikują dane, kody lokacji w lesie usługi Active Directory musi być unikatowa, nawet jeśli są używane w innej hierarchii programu Configuration Manager lub jeśli były używane w przypadku wcześniejszej instalacji programu Configuration Manager. Należy dokładnie zaplanować kody i nazwy lokacji przed wdrożeniem hierarchii.

### <a name="specify-a-site-code-and-site-name"></a>Określ kod i nazwę lokacji
Po uruchomieniu Instalatora programu Configuration Manager, zostanie wyświetlony monit o kod i nazwę lokacji centralnej lokacji administracyjnej, a dla każdej lokacji głównej i instalacja lokacji dodatkowej. Kod lokacji musi unikatowo zidentyfikować każdej lokacji w hierarchii. Ponieważ kody lokacji są używane w nazwach folderów, nie wolno używać następujące nazwy dla kodu lokacji, w tym nazwy zastrzeżone dla programu Configuration Manager i systemu Windows:
  -  AUX
  -  CON
  -  NUL
  -  PRN
  -  SMS

> [!NOTE]
> Instalator programu Configuration Manager nie weryfikuje, że kod lokacji nie jest już w użyciu.

Aby wprowadzić kod lokacji dla lokacji, po uruchomieniu Instalatora programu Configuration Manager, należy wprowadzić trzy znaki alfanumeryczne. Tylko litery *A* za pośrednictwem *Z* i numery *0* za pośrednictwem *9*, w dowolnej kombinacji są dozwolone w kodów lokacji. Sekwencja liter i cyfr nie ma znaczenia dla komunikacji między lokacjami. Na przykład, nie jest konieczne nazwanie lokacji głównej *ABC* a lokacją dodatkową *DEF*.

Nazwa lokacji jest to przyjazna nazwa identyfikująca dla lokacji. Można używać tylko znaki *A* za pośrednictwem *Z*, ** za pośrednictwem *z*, *0* za pośrednictwem *9*oraz łącznik (*-*) w nazwach lokacji.

> [!IMPORTANT]
> Zmiana nazwy lokacji po zainstalowaniu lokacji lub kod lokacji nie jest obsługiwane.

### <a name="reuse-a-site-code"></a>Ponowne użycie kodu lokacji
Kody lokacji nie można użyć więcej niż jeden raz w hierarchii programu Configuration Manager dla centralnej lokacji administracyjnej lub lokacji głównej, nawet jeśli pierwotnej lokacji i kod został odinstalowany. Ponowne użycie kodu lokacji ryzyko konfliktem ID obiektów w hierarchii. Jeśli w tej lokacji dodatkowej i kod lokacji nie są już używane w hierarchii programu Configuration Manager lub w lesie usługi Active Directory, można użyć ponownie kod lokacji dla lokacji dodatkowej.

## <a name="limits-and-restrictions-for-installed-sites"></a>Ograniczenia dla witryn zainstalowanych i limity
Przed zainstalowaniem lokacji należy zrozumieć następujące ograniczenia, które są stosowane do lokacji i hierarchii w lokacji:
-   Po zakończeniu instalacji następujące właściwości lokacji nie można zmienić bez odinstalowania lokacji i zainstalować go ponownie przy użyciu nowych wartości:  
  -   Katalogu instalacyjnego plików programu  
  -   Kod lokacji  
  -   Opis witryny  
-   Gdy hierarchii obejmuje centralnej lokacji administracyjnej:  
  -   Menedżer konfiguracji nie obsługuje przenoszenia podrzędną lokację główną z hierarchii, aby utworzyć autonomicznej lokacji głównej lub dołączyć ją do innej hierarchii. Zamiast tego odinstaluj podrzędnej lokacji głównej, a następnie zainstaluj go ponownie jako autonomicznej nowej lokacji głównej lub lokacją podrzędną centralnej lokacji administracyjnej z innej hierarchii.  


## <a name="bkmk_optionalsteps"></a>Opcjonalne czynności przed uruchomieniem Instalatora
**Ręcznie uruchom [Narzędzie pobierania Instalatora](../../../../core/servers/deploy/install/setup-downloader.md)**

Aby pobrać zaktualizowane pliki Instalatora programu Configuration Manager, można uruchomić Narzędzie pobierania Instalatora. Jeśli komputer, na którym spowoduje uruchomienie Instalatora nie jest połączony z Internetem lub jeśli chcesz zainstalować wiele serwerów lokacji, należy rozważyć użycie narzędzia pobierania Instalatora pobrać wymagane aktualizacje do Instalatora. Poniżej przedstawiono dodatkowe informacje:
-  Domyślnie Instalator łączy się z Internetem, aby pobrać zaktualizowane pliki Instalatora.
-  Domyślnie pliki są przechowywane w folderze Redist.
-  Ustawienia można kierować do lokalizacji w sieci, w którym są przechowywane wcześniej kopii tych plików.

**Ręcznie uruchom [narzędzie sprawdzania wymagań wstępnych](../../../../core/servers/deploy/install/prerequisite-checker.md)**

Aby zidentyfikować i rozwiązać problemy przed uruchomieniem Instalatora, aby zainstalować lokację oraz przed zainstalowaniem roli systemu lokacji na serwerze, należy uruchomić narzędzie sprawdzania wymagań wstępnych. Narzędzie sprawdzania wymagań wstępnych pomaga zapewnić, że komputer spełnia wymagania dotyczące hosta lokacji lub rola systemu lokacji. Poniżej przedstawiono dodatkowe informacje:
 -  Domyślnie Instalator uruchamia narzędzie sprawdzania wymagań wstępnych.
 -  Jeśli wystąpią jakieś błędy, Instalator zatrzymuje, dopóki problem nie zostanie rozwiązany.

**Określić opcjonalne portów**

Można określić opcjonalne porty dla systemów lokacji i klientów do użycia. Poniżej przedstawiono dodatkowe informacje:
 -  Systemy lokacji i klientów domyślnie używają portów wstępnie zdefiniowane do komunikacji.
 -  Podczas instalacji można skonfigurować alternatywne porty.

 Aby uzyskać więcej informacji, zobacz [portów używanych w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/ports.md).

