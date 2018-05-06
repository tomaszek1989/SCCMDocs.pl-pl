---
title: Klient równorzędnej pamięci podręcznej
titleSuffix: Configuration Manager
description: Używanie równorzędnej pamięci podręcznej dla lokalizacji źródła zawartości klienta podczas wdrażania zawartości w programie System Center Configuration Manager.
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b705a2cb8eccae3abe63c5de0680c712ab2e181e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="peer-cache-for-configuration-manager-clients"></a>Buforowania równorzędnego klientów programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

<!--1101436-->
Użyj **równorzędnej pamięci podręcznej** pomagające w zarządzaniu wdrażaniem zawartości dla klientów w lokalizacjach zdalnych. Równorzędna pamięć podręczna jest wbudowanego rozwiązania programu Configuration Manager, która umożliwia klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.   

> [!TIP]  
> Ta funkcja została wprowadzona w wersji 1610 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1710, ta funkcja nie jest już funkcji wersji wstępnej.  


> [!Note]  
> Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


## <a name="overview"></a>Omówienie
Klient równorzędnej pamięci podręcznej jest możliwość używania równorzędnej pamięci podręcznej klienta programu Configuration Manager. Równorzędnej pamięci podręcznej, który klient, który ma on zawartości mogą udostępniać dodatkowe klientach jest źródłem równorzędnej pamięci podręcznej.
 -  Aby umożliwić klientom równorzędnej pamięci podręcznej można użyć ustawień klienta.
 -  Aby udostępnić zawartość jako źródło równorzędnej pamięci podręcznej, klient równorzędnej pamięci podręcznej:
    -  Muszą być przyłączone do domeny. Jednak klient, który nie jest przyłączony do domeny mogą pobierać zawartość z domeny częścią źródła równorzędnej pamięci podręcznej.
    -  Musi należeć do bieżącej grupy granic klienta, który jest wyszukiwanie zawartości. Gdy klient użyje powrotu do wyszukania zawartości z grupą granic sąsiada, listy lokalizacji źródła zawartości nie ma w grupie granic sąsiada równorzędnej pamięci podręcznej klienta. Aby uzyskać więcej informacji o grupach granic bieżących i sąsiada, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - Klient programu Configuration Manager służy każdego typu zawartości w pamięci podręcznej dla innych klientów przy użyciu równorzędnej pamięci podręcznej. Ta zawartość zawiera pliki usługi Office 365 i określa pliki instalacyjne.<!--SMS.500850-->
 -  Równorzędna pamięć podręczna nie zastępuje użycia innych rozwiązań, takich jak usługi BranchCache. Równorzędnej pamięci podręcznej działa wraz z innych rozwiązań więcej opcji rozszerzenia tradycyjnych rozwiązań wdrażania zawartości takie jak punkty dystrybucji. Równorzędna pamięć podręczna jest rozwiązanie niestandardowe z nie zależy od usługi BranchCache. Jeśli nie włączysz lub użyć usługi Windows BranchCache, równorzędnej pamięci podręcznej nadal działa.

### <a name="operations"></a>Operacje

Aby włączyć równorzędną pamięć podręczną, Wdróż ustawienia klienta w kolekcji. Elementy członkowskie tej kolekcji działa jako źródło zawartości elementu równorzędnego dla innych klientów w tej samej grupy granic.
 -  Klient, który działa jako źródło zawartości równorzędnej przesyła listy dostępnej zawartości pamięci podręcznej do swojego punktu zarządzania.
 -  Gdy następny klient w tej grupie granic zażąda zawartości, każdego źródła równorzędnej pamięci podręcznej, zawartość i jest w trybie online, jest zwracana na liście potencjalne źródła zawartości. Ta lista zawiera również punkty dystrybucji i innych lokalizacji źródła zawartości z tej grupy granic.
 -  Na normalny proces klienta, który jest wyszukiwanie zawartości wybiera jedno źródło z podaną listą. Następnie klient próbuje pobrać zawartość.

> [!NOTE]
> Jeśli klient przechodzi do grupy granic sąsiada dla zawartości, nie dodaje lokalizacji źródła zawartości równorzędnej pamięci podręcznej sąsiada grupy granic do listy potencjalnych lokalizacji źródła zawartości.  


Najlepszym rozwiązaniem jest, aby wybrać tylko klienci najodpowiedniejszy źródłem równorzędnej pamięci podręcznej. Ocenia przydatność klienta na podstawie atrybutów, takich jak typ obudowy, miejsca na dysku i łączność sieciową. Aby uzyskać więcej informacji, które mogą pomóc w Wybierz najlepsze klientów do użycia na potrzeby równorzędnej pamięci podręcznej, zobacz [ten blog przez konsultanta Microsoft](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Ograniczony dostęp do źródła równorzędnej pamięci podręcznej**  
Począwszy od wersji 1702 komputerze źródła równorzędnej pamięci podręcznej odrzuca żądania dotyczące zawartości, jeśli komputer źródłowy równorzędnej pamięci podręcznej spełnia żadnego z następujących warunków:  
  -  Jest w trybie niskim poziomie naładowania baterii.
  -  Obciążenie procesora CPU przekracza 80% w czasie żądanej zawartości.
  -  We/Wy dysku ma *AvgDiskQueueLength* przekraczający 10.
  -  Brak dostępnego połączenia z tym komputerem.   

Konfigurowanie tych ustawień za pomocą serwera konfiguracji klienta klasy usługi WMI funkcji źródło elementu równorzędnego (*SMS_WinPEPeerCacheConfig*) w zestawie SDK programu Configuration Manager.

Gdy komputer odrzuci zawartości, komputera wysyłającego żądanie w dalszym ciągu wyszukiwania zawartości z listy lokalizacji źródła zawartości.   



### <a name="monitoring"></a>Monitorowanie   
Aby ułatwić zrozumienie użycia równorzędnej pamięci podręcznej, można wyświetlić pulpit nawigacyjny źródła danych klienta. Zobacz [źródła danych klienta pulpitu nawigacyjnego](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

Począwszy od wersji 1702, można użyć trzech raportów do wyświetlania użycie pamięci podręcznej elementów równorzędnych. W konsoli przejdź do **monitorowanie** > **raportowania** > **raporty**. Wszystkie raporty mają typ **zawartości dystrybucji oprogramowania**:
1.  **Elementu równorzędnego pamięci podręcznej źródła zawartości odrzucenia**:  
Ten raport służy do zrozumienia, jak często źródła równorzędnej pamięci podręcznej w grupie granic odrzucać żądania zawartości.
 - **Znany problem:** Gdy przechodzenie na wyniki, takich jak *MaxCPULoad* lub *MaxDiskIO*, zostanie zgłoszony błąd, które sugeruje raportu lub nie można znaleźć szczegółowe informacje. Aby obejść ten problem, należy użyć następujące dwa raporty, które bezpośrednio Pokaż wyniki.

2. **Elementu równorzędnego odrzucenia zawartości w pamięci podręcznej źródło przez warunek**:  
Ten raport umożliwia poznać szczegóły odrzucenia dla typu grupy lub odrzucenia określonej granicy. Można określić

  - **Znany problem:** Nie można wybierać z dostępnych parametrów, a zamiast tego należy wprowadzić je ręcznie. Wprowadź wartości w polach *Nazwa grupy granic* i *typu odrzucenia* w pierwszym raportu. Na przykład w przypadku *typu odrzucenia* może wprowadzić *MaxCPULoad* lub *MaxDiskIO*.

3. **Elementu równorzędnego pamięci podręcznej źródła zawartości odrzucenia szczegóły**:   
  Ten raport służy do zrozumienia zawartość, która zażądano klienta, gdy odrzucona.

 - **Znany problem:** Nie można wybierać z dostępnych parametrów, a zamiast tego należy wprowadzić je ręcznie. Wprowadź wartość dla *typu odrzucenia* wyświetlaną w **elementu równorzędnego pamięci podręcznej źródła zawartości odrzucenia** raportu. Następnie wprowadź *identyfikator zasobu* dla źródła zawartości, o którym chcesz uzyskać więcej informacji. Aby znaleźć identyfikator zasobu źródła zawartości:  

    1. Znajdowanie nazwy komputera, który będzie wyświetlany jako *źródła równorzędnej pamięci podręcznej* w wynikach **elementu równorzędnego odrzucenia zawartości w pamięci podręcznej źródło przez warunek** raportu.  
    2. Następnie należy przejść do **zasoby i zgodność** > **urządzeń** , a następnie wyszukaj tej nazwy komputerów. Użyj wartości w kolumnie Identyfikator zasobu.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Wymagania i uwagi dotyczące równorzędnej pamięci podręcznej
-   Równorzędna pamięć podręczna jest obsługiwana na systemie operacyjnym Windows, który jest obsługiwany jako klient programu Configuration Manager. Bez systemu operacyjnego nie są obsługiwane dla równorzędnej pamięci podręcznej.

-   Tylko klienci mogą przesyłać zawartość, od klientów równorzędnej pamięci podręcznej, które znajdują się w ich bieżącej grupy granic.

-   Przed wersją 1706 każdej lokacji, w którym klienci używają równorzędnej pamięci podręcznej musi być skonfigurowany z [konta dostępu do sieci](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). Począwszy od wersji 1706, że konto nie jest już wymagane z jednym wyjątkiem. Scenariusz wyjątku jest w przypadku elementu równorzędnego z obsługą pamięci podręcznej klient uruchamia sekwencję zadań z Centrum oprogramowania, a sekwencja zadań wykonuje ponowny rozruch do obrazu rozruchowego. W tym scenariuszu klient nadal wymaga konta dostępu do sieci. Jeśli klient znajduje się w środowisku Windows PE, używa konta dostępu do sieci pobierać zawartość ze źródła równorzędnej pamięci podręcznej.

    Gdy jest to wymagane, komputer źródła równorzędnej pamięci podręcznej używa konta dostępu do sieci do uwierzytelniania żądań pobierania od elementów równorzędnych. To konto wymaga tylko uprawnienia użytkownika domeny, w tym celu.

-   Ostatni przesłanie spisu sprzętu klienta Określa bieżący granic źródła zawartości równorzędnej pamięci podręcznej. Klient, który uzyskuje mobilny dostęp do grupy granic różnych nadal może być członkiem grupy granic wcześniejsze na potrzeby równorzędnej pamięci podręcznej. Powoduje to zachowanie klienta oferowany źródła zawartości równorzędnej pamięci podręcznej, który nie znajduje się w lokalizacji bezpośredniej sieci. Firma Microsoft zaleca, z wyjątkiem klientów, którzy są podatne na tej konfiguracji z uczestnictwa jako źródło równorzędnej pamięci podręcznej.
-    Począwszy od wersji 1706, klient równorzędnej pamięci podręcznej najpierw sprawdza, czy źródło zawartości równorzędnej pamięci podręcznej online przed próbą pobrania zawartości. <!--sms.498675-->

## <a name="to-configure-client-peer-cache-client-settings"></a>Aby skonfigurować ustawienia klienta buforowania równorzędnego klienta
Aby uzyskać informacje o konfigurowaniu ustawień klienta, zobacz [ustawienia pamięci podręcznej klienta](/sccm/core/clients/deploy/about-client-settings#client-cache-settings). Aby uzyskać więcej informacji, zobacz [sposób konfigurowania ustawień klienta](/sccm/core/clients/deploy/configure-client-settings).

Na równorzędnej pamięci podręcznej klientów obsługujących używanych przez zaporę systemu Windows programu Configuration Manager konfiguruje porty zapory, które określają w ustawieniach klienta.
