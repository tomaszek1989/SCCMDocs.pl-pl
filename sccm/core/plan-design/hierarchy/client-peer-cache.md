---
title: "Klient równorzędnej pamięci podręcznej"
titleSuffix: Configuration Manager
description: "Używanie równorzędnej pamięci podręcznej dla lokalizacji źródła zawartości klienta podczas wdrażania zawartości w programie System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 20438f51a67fb29da21c879620870caf3328121d
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="peer-cache-for-configuration-manager-clients"></a>Buforowania równorzędnego klientów programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie System Center Configuration Manager wersji 1610, można użyć **równorzędnej pamięci podręcznej** pomagające w zarządzaniu wdrażaniem zawartości dla klientów w lokalizacjach zdalnych. Równorzędna pamięć podręczna jest wbudowanego rozwiązania programu Configuration Manager, która umożliwia klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.   

> [!TIP]  
> Wprowadzonym w wersji 1610, równorzędnej pamięci podręcznej i pulpit nawigacyjny źródła danych klienta są funkcje wersji wstępnej. Aby je włączyć, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/pre-release-features).

## <a name="overview"></a>Omówienie
Klient równorzędnej pamięci podręcznej jest możliwość używania równorzędnej pamięci podręcznej klienta programu Configuration Manager. Równorzędnej pamięci podręcznej, który klient, który ma on zawartości mogą udostępniać dodatkowe klientach jest źródłem równorzędnej pamięci podręcznej.
 -  Aby umożliwić klientom równorzędnej pamięci podręcznej można użyć ustawień klienta.
 -  Aby udostępnić zawartość jako źródło równorzędnej pamięci podręcznej, klient równorzędnej pamięci podręcznej:
    -  Muszą być przyłączone do domeny. Jednak klient, który nie jest przyłączony do domeny mogą pobierać zawartość z domeny częścią źródła równorzędnej pamięci podręcznej.
    -  Musi należeć do bieżącej grupy granic klienta, który jest wyszukiwanie zawartości. Klient równorzędnej pamięci podręcznej sąsiada grupy granic nie jest dołączony puli lokalizacji źródła zawartości, gdy klient użyje powrotu do wyszukania zawartości z grupą granic sąsiedniego. Aby uzyskać więcej informacji o grupach granic bieżących i sąsiada, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - Każdy typ zawartości, która jest przechowywana w pamięci podręcznej klienta programu Configuration Manager mogą być udostępniane innym klientom przy użyciu równorzędnej pamięci podręcznej.
 -  Buforowanie równorzędne nie zastępuje użycia innych rozwiązań, takich jak usługi BranchCache, ale działa side-by-side z nim więcej opcji rozszerzenia tradycyjnych rozwiązań wdrażania zawartości takie jak punkty dystrybucji. Jest to rozwiązanie niestandardowe z nie zależy od usługi BranchCache, więc jeśli nie włączysz lub użyć usługi Windows BranchCache, nadal działa.

### <a name="operations"></a>Operacje

Po wdrożeniu ustawień klienta umożliwiających Buforowanie równorzędne kolekcji elementy członkowskie tej kolekcji może działać jako źródło zawartości elementu równorzędnego dla innych klientów w tej samej grupy granic:
 -  Klient, który działa jako źródło zawartości równorzędnej przesyła listy dostępnej zawartości pamięci podręcznej do swojego punktu zarządzania.
 -  Następnie gdy następny klient w tej grupie granic zażąda zawartości, każdego źródła równorzędnej pamięci podręcznej, który ma zawartość jest zwracana jako potencjalne źródła zawartości wraz z punktów dystrybucji i innych lokalizacji źródła zawartości z tej grupy granic.
 -  Na normalny proces działania klient, który jest wyszukiwanie zawartości wybiera jedno źródło zawartości z puli źródeł udostępnił, a następnie przechodzi do próbę pobrania zawartości.

> [!NOTE]
> Jeśli powrotu do grupy granic sąsiada dla zawartości występuje, równorzędna pamięć podręczna lokalizacji źródła zawartości z grupą granic sąsiada nie są dodawane do puli klienta potencjalnych lokalizacji źródła zawartości.  


Chociaż możesz wprowadzić wszyscy klienci uczestniczyć jako źródło równorzędnej pamięci podręcznej, to jest najlepiej wybrać tylko w przypadku klientów, które najlepiej nadaje się do trwa równorzędnej pamięci podręcznej źródeł.  Przydatności klientów można ocenić na podstawie typ obudowy do klienta, miejsca na dysku, łączności sieciowej i. Aby uzyskać więcej informacji, które mogą pomóc w Wybierz najlepsze klientów do użycia na potrzeby równorzędnej pamięci podręcznej, zobacz [ten blog przez konsultanta Microsoft](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Ograniczony dostęp do źródła równorzędnej pamięci podręcznej**  
Począwszy od wersji 1702 komputerze źródła równorzędnej pamięci podręcznej żądania zawartości podczas odrzuci komputer źródłowy równorzędnej pamięci podręcznej spełnia żadnego z następujących warunków:  
  -  Jest w trybie niskim poziomie naładowania baterii.
  -  Obciążenie procesora CPU przekracza 80% w czasie żądanej zawartości.
  -  We/Wy dysku ma *AvgDiskQueueLength* przekraczający 10.
  -  Brak dostępnego połączenia z tym komputerem.   

Można skonfigurować te ustawienia przy użyciu serwera konfiguracji klienta klasy usługi WMI dla funkcji źródło elementu równorzędnego (*SMS_WinPEPeerCacheConfig*) gdy używasz zestawu SDK System Center Configuration Manager.

Gdy komputer odrzuci zawartości, komputera wysyłającego żądanie będzie wyszukiwanie zawartości z alternatywnych źródeł w puli lokalizacji źródła zawartości.   



### <a name="monitoring"></a>Monitorowanie   
Aby ułatwić zrozumienie użycia równorzędnej pamięci podręcznej, można wyświetlić pulpit nawigacyjny źródła danych klienta. Zobacz [źródła danych klienta pulpitu nawigacyjnego](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

Począwszy od wersji 1702, można użyć trzech raportów do wyświetlania użycie pamięci podręcznej elementów równorzędnych. W konsoli przejdź do **monitorowanie** > **raportowania** > **raporty**. Wszystkie raporty mają typ **zawartości dystrybucji oprogramowania**:
1.  **Elementu równorzędnego pamięci podręcznej źródła zawartości odrzucenia**:  
Ten raport służy do zrozumienia, jak często źródła równorzędnej pamięci podręcznej w grupie granic odrzucił żądanie zawartości.
 - **Znany problem:** Gdy przechodzenie na wyniki, takich jak *MaxCPULoad* lub *MaxDiskIO*, zostanie zgłoszony błąd, które sugeruje raportu lub nie można znaleźć szczegółowe informacje. Aby obejść ten problem, należy użyć następujące dwa raporty, które bezpośrednio Pokaż wyniki.

2. **Elementu równorzędnego odrzucenia zawartości w pamięci podręcznej źródło przez warunek**:  
Ten raport umożliwia poznać szczegóły odrzucenia dla typu grupy lub odrzucenia określonej granicy. Można określić

  - **Znany problem:** Nie można wybierać z dostępnych parametrów, a zamiast tego należy wprowadzić je ręcznie. Wprowadź wartości w polach *Nazwa grupy granic* i *typu odrzucenia* w pierwszym raportu. Na przykład w przypadku *typu odrzucenia* może wprowadzić *MaxCPULoad* lub *MaxDiskIO*.

3. **Elementu równorzędnego pamięci podręcznej źródła zawartości odrzucenia szczegóły**:   
  Ten raport służy do zrozumienia zawartość, która została żądanej, jeśli został on odrzucony.

 - **Znany problem:** Nie można wybierać z dostępnych parametrów, a zamiast tego należy wprowadzić je ręcznie. Wprowadź wartość dla *typu odrzucenia* wyświetlaną w pierwszym raportu (równorzędnej pamięci podręcznej źródła zawartości odrzucenia), a następnie wprowadź *identyfikator zasobu* dla źródła zawartości, który chcesz uzyskać więcej informacji o.  Aby znaleźć identyfikator zasobu źródła zawartości:  

    1. Znajdowanie nazwy komputera, który będzie wyświetlany jako *źródła równorzędnej pamięci podręcznej* w wynikach raportu 2 (równorzędnej pamięci podręcznej źródła zawartości odrzucenia warunek).  
    2. Następnie należy przejść do **zasoby i zgodność** > **urządzeń** , a następnie wyszukaj tej nazwy komputerów. Użyj wartości w kolumnie Identyfikator zasobu.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Wymagania i uwagi dotyczące równorzędnej pamięci podręcznej
-   Równorzędna pamięć podręczna jest obsługiwana na systemie operacyjnym Windows, który jest obsługiwany jako klient programu Configuration Manager. Bez systemu operacyjnego nie są obsługiwane dla równorzędnej pamięci podręcznej.

-   Tylko klienci mogą przesyłać zawartość, od klientów równorzędnej pamięci podręcznej, które znajdują się w ich bieżącej grupy granic.

-   Przed wersją 1706 każdej lokacji, w którym klienci używają równorzędnej pamięci podręcznej musi być skonfigurowany z [konta dostępu do sieci](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). Począwszy od wersji 1706, że konto nie jest już wymagane z jednym wyjątkiem.  Wyjątek stanowi, gdy klient używa równorzędnej pamięci podręcznej, pobieranie i uruchamianie sekwencji zadań z Centrum oprogramowania, a sekwencja zadań wykonuje ponowny rozruch klienta w środowisku WinPE.  W tym scenariuszu klient nadal wymaga konta dostępu do sieci, gdy jest w środowisku WinPE, dzięki czemu można uzyskać dostępu do źródła równorzędnej pamięci podręcznej, aby pobrać zawartość.

    Gdy jest to wymagane, konto dostępu do sieci jest używany przez komputer źródła równorzędnej pamięci podręcznej do uwierzytelniania żądań pobierania od elementów równorzędnych i wymaga tylko uprawnienia użytkownika domeny, w tym celu.

-   Ponieważ bieżącego granic źródła równorzędnej pamięci podręcznej zawartości jest określany przez ostatnich przesłanie spisu sprzętu tego klienta, klient uzyskuje mobilny dostęp do lokalizacji sieciowej, który znajduje się w grupie granic różnych może być brany pod członka grupy granic wcześniejsze na potrzeby równorzędnej pamięci podręcznej. Może to spowodować, że klient oferowany źródła zawartości równorzędnej pamięci podręcznej, który nie znajduje się w lokalizacji bezpośredniej sieci. Firma Microsoft zaleca, z wyjątkiem klientów, którzy są podatne na tej konfiguracji z uczestnictwa jako źródło równorzędnej pamięci podręcznej.

## <a name="to-configure-client-peer-cache-client-settings"></a>Aby skonfigurować ustawienia klienta buforowania równorzędnego klienta
1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **ustawień klienta**, a następnie otwórz obiekt ustawień klienta urządzenia, którego chcesz używać. Można również zmodyfikować obiekt domyślne ustawienia klienta.
2.  Z listy dostępnych ustawień, wybierz **ustawienia pamięci podręcznej klienta**.
3.  Ustaw **klienta Włącz program Configuration Manager w pełnej wersji systemu operacyjnego, aby udostępnić zawartość** do **tak**.
4.  Skonfiguruj następujące ustawienia, aby zdefiniować porty, które ma być używany na potrzeby równorzędnej pamięci podręcznej:  
  -  **Port początkowego rozgłaszania sieciowego**
  -  **Włącz protokół HTTPS dla komunikacji równorzędnej między klientami**
  -  **Port pobierania zawartości z elementu równorzędnego (HTTP/HTTPS)**

Na każdym komputerze, na którym włączono obsługę równorzędnej pamięci podręcznej Jeśli jest używana Zapora systemu Windows, programu Configuration Manager konfiguruje Aby zezwolić na korzystanie z portów, które można skonfigurować.
