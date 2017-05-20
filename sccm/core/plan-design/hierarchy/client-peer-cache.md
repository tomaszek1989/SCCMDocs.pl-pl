---
title: "Buforowanie równorzędne klienta | System Center Configuration Manager"
description: "Użyj Buforowanie równorzędne dla lokalizacji źródła zawartości klienta podczas wdrażania zawartości z System Center Configuration Manager."
ms.custom: na
ms.date: 4/4/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 86cd5382-8b41-45db-a4f0-16265ae22657
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: dcd05d7d120f8997562da7d92b38c8b52a512357
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="peer-cache-for-configuration-manager-clients"></a>Buforowanie równorzędne dla klientów programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od z System Center Configuration Manager w wersji 1610, można użyć **Buforowanie równorzędne** aby ułatwić Zarządzanie wdrażaniem zawartości do klientów w lokalizacjach zdalnych. Buforowanie równorzędne jest wbudowane rozwiązanie programu Configuration Manager, które umożliwia klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.   

> [!TIP]  
> Wprowadzona w wersji 1610, Buforowanie równorzędne i pulpit nawigacyjny źródeł danych klientów są funkcje wersji wstępnej. Aby je włączyć, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/pre-release-features).

## <a name="overview"></a>Omówienie
 -     Klienci mogą używać Buforowanie równorzędne można użyć ustawień klienta.
 -     Aby udostępnić zawartość, Buforowanie równorzędne klientów zarówno należy członków bieżącej grupy granic klienta, który jest przeszukiwanie zawartości. Peer pamięci podręcznej klienci w grupach granic sąsiada nie są uwzględniane z pulą lokalizacji źródła zawartości, gdy klient używa powrotu do odszukania zawartości z grupą granic sąsiada. Aby uzyskać więcej informacji o grupach granic bieżących i sąsiada, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups##a-namebkmkboundarygroupsa-boundary-groups).
 - Klienci, którzy nie są włączone dla Buforowanie równorzędne, ale są w bieżącej grupie granic z Buforowanie równorzędne włączono klientów, może pobierać zawartość z klienta włączone buforowanie równorzędne.  
 - Każdy typ zawartości, który jest przechowywany w pamięci podręcznej klienta programu Configuration Manager może zostać wysłany do innych klientów przy użyciu Buforowanie równorzędne.
 -    Buforowanie równorzędne zastępuje użycie innych rozwiązań, takich jak usługi BranchCache, lecz zamiast tego działa side-by-side z nim więcej opcji rozszerzania rozwiązań tradycyjne rozmieszczania zawartości, takich jak punkty dystrybucji. Jest to rozwiązanie z niestandardowych nie zależy od usługi BranchCache, więc jeśli nie zostanie włączone lub użyć usługi Windows BranchCache, nadal działa.

### <a name="operations"></a>Operacje

Po wdrożeniu ustawień klienta, które umożliwiają Buforowanie równorzędne w kolekcji członków tej kolekcji może działać jako źródła zawartości elementu równorzędnego dla innych klientów w tej samej grupie granic:
 -    Klient, który działa jako źródło zawartości elementu równorzędnego przesyła listę dostępnych zawartość z pamięci podręcznej do swojego punktu zarządzania.
 -    Następnie gdy następny klient w tej grupie granic żąda tej zawartości, każde źródło pamięci podręcznej elementu równorzędnego, którego zawartość jest zwracany jako potencjalne źródła zawartości wraz z punktów dystrybucji i innych lokalizacji źródła zawartości z tej grupy granic.
 -    Na normalny proces działania klient, który jest wyszukiwanie zawartości wybiera jednego źródła zawartości z puli źródła dostarczył, a następnie przechodzi do próbę pobrania zawartości.

> [!NOTE]
> W przypadku powrotu do grupy granic sąsiada zawartości występuje, Buforowanie równorzędne lokalizacji źródła zawartości z grupą granic sąsiada nie są dodawane do puli klienta potencjalnych lokalizacji źródła zawartości.  


Chociaż istnieje możliwość wszyscy klienci uczestniczyć jako źródło pamięci podręcznej elementów równorzędnych, to jest najlepszym rozwiązaniem, aby wybrać tylko w przypadku klientów, którzy są najlepsze odpowiednie dla trwa peer źródeł pamięci podręcznej.  Na podstawie typ obudowy klienta, miejsce na dysku, połączenie sieciowe i można oszacować przydatności klientów. Aby uzyskać więcej informacji, które mogą pomóc wybrać najlepsze klientów na potrzeby Buforowanie równorzędne, zobacz [ten blog przez konsultanta Microsoft](https://blogs.technet.microsoft.com/setprice/2016/06/29/pe-peer-cache-custom-reporting-examples/).

**Ograniczony dostęp do źródła pamięci podręcznej elementu równorzędnego**  
Począwszy od wersji 1702 komputera źródłowego pamięci podręcznej elementu równorzędnego będą odrzucać żądania zawartości, gdy komputer źródłowy pamięci podręcznej elementu równorzędnego spełnia żadnego z następujących warunków:  
  -  Jest w trybie niskim poziomie naładowania baterii.
  -  Obciążenie procesora CPU przekracza 80% w czasie żądania zawartości.
  -  We/Wy dysku ma *AvgDiskQueueLength* który przekracza 10.
  -  Nie ma ma więcej dostępnych połączeń z komputerem.   

Można skonfigurować te ustawienia przy użyciu klasy WMI serwera konfiguracji klienta dla funkcji źródło równorzędnego (*SMS_WinPEPeerCacheConfig*) używając System Center Configuration Manager SDK.

Gdy komputer odrzuci zawartość, komputera wysyłającego żądanie będzie wyszukiwać zawartość z alternatywnych źródeł w puli lokalizacji źródła zawartości.   



### <a name="monitoring"></a>Monitorowanie   
Ułatwią zrozumienie stosowania Buforowanie równorzędne, można wyświetlić pulpit nawigacyjny źródeł danych klientów. Zobacz [pulpitu nawigacyjnego źródeł danych klientów](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).

Począwszy od wersji 1702, można użyć trzy raporty do wyświetlania elementów równorzędnych użycia pamięci podręcznej. W konsoli, przejdź do **monitorowanie** > **raportowania** > **raporty**. Wszystkie raporty mają typ **zawartości dystrybucji oprogramowania**:
1.  **Peer odrzucenia zawartości pamięci podręcznej źródła**:  
Ten raport umożliwia zrozumienie, jak często źródła pamięci podręcznej elementów równorzędnych w grupie granic odrzucił żądanie zawartości.
 - **Znany problem:** Podczas przechodzenia na wyniki, takich jak *MaxCPULoad* lub *MaxDiskIO*, może zostać wyświetlony błąd sugerujące, raportu lub nie można odnaleźć szczegółów. Aby obejść ten problem, użyj następujących dwóch raporty, które bezpośrednio Pokaż wyniki.

2. **Peer odrzucenia zawartości pamięci podręcznej źródła warunek**:  
Ten raport umożliwia poznać szczegóły odrzucenia dla typu grupy lub odrzucenia określonej granicy. Można określić

  - **Znany problem:** Nie można wybierać z dostępnych parametrów i zamiast tego należy wprowadzić je ręcznie. Wpisz wartości dla *Nazwa grupy granic* i *typu odrzucenia* w pierwszym raportu. Na przykład w przypadku *typu odrzucenia* wprowadzić *MaxCPULoad* lub *MaxDiskIO*.

3. **Peer szczegóły odrzucenia zawartości pamięci podręcznej źródła**:   
  Ten raport służy do zrozumienia zawartość, która została żądanego podczas został odrzucony.

 - **Znany problem:** Nie można wybierać z dostępnych parametrów i zamiast tego należy wprowadzić je ręcznie. Wprowadź wartość dla *typu odrzucenia* wyświetlanych w pierwszym raportu (Peer pamięci podręcznej źródła zawartości o odrzuceniu), a następnie wprowadź *identyfikator zasobu* dla źródła zawartości, który chcesz uzyskać więcej informacji o.  Aby znaleźć identyfikator zasobu źródła zawartości:  

    1. Znajdź nazwę komputera, który będzie wyświetlany jako *źródła pamięci podręcznej elementu równorzędnego* w wynikach raportu 2 (Peer pamięci podręcznej źródła zawartości o odrzuceniu warunek).  
    2. Następnie należy przejść do **zasoby i zgodność** > **urządzeń** i następnie wyszukiwania dla tej nazwy komputerów. Użyj wartości w kolumnie Identyfikator zasobu.  


## <a name="requirements-and-considerations-for-peer-cache"></a>Wymagania i uwagi dotyczące pamięci podręcznej elementu równorzędnego
-   Buforowanie równorzędne jest obsługiwany w systemie operacyjnym Windows obsługiwana jako klient programu Configuration Manager. Bez systemu operacyjnego nie są obsługiwane przez pamięć podręczną elementów równorzędnych.

-   Tylko klienci mogą przesyłać zawartość, Buforowanie równorzędne klientom, którzy są w ich bieżącej grupy granic.

-   Każda lokacja, w której klienci używają Buforowanie równorzędne musi być skonfigurowany z [konta dostępu do sieci](/sccm/core/plan-design/hierarchy/manage-accounts-to-access-content#a-namebkmknaaa-network-access-account). Konto jest używane przez komputer źródłowy Buforowanie równorzędne do uwierzytelniania żądań pobierania z elementami równorzędnymi i wymaga tylko uprawnienia użytkownika domeny do tego celu.

-     Ponieważ bieżący granic Buforowanie równorzędne źródła zawartości jest określany przez ostatnich przesłanie spisu sprzętu tego klienta, klient przejdzie do lokalizacji sieciowej, który znajduje się w grupie granic różnych może została uznana za do jego grupy granic były do celów Buforowanie równorzędne. Może to spowodować klienta oferowany Buforowanie równorzędne źródła zawartości, która nie znajduje się w lokalizacji bezpośredniej sieci. Firma Microsoft zaleca, z wyjątkiem klientów, które są podatne na tej konfiguracji z uczestnictwa w postaci źródła Buforowanie równorzędne.

## <a name="to-configure-client-peer-cache-client-settings"></a>Aby skonfigurować ustawienia klienta pamięci podręcznej klienta elementów równorzędnych
1.    W konsoli programu Configuration Manager, przejdź do **Administracja** > **ustawień klienta**, a następnie otwórz obiekt ustawień klienta urządzenia, którego chcesz używać. Można również zmodyfikować obiekt domyślne ustawienia klienta.
2.    Wybrać z listy dostępnych ustawień, **ustawienia pamięci podręcznej klienta**.
3.    Ustaw **klienta programu Configuration Manager Włącz w pełnej wersji systemu operacyjnego na współużytkowanie zawartości** do **tak**.
4.    Skonfiguruj następujące ustawienia, aby zdefiniować porty, które chcesz użyć dla elementów równorzędnych w pamięci podręcznej:  
  -  **Port początkowego rozgłaszania sieciowego**
  -  **Włączyć protokół HTTPS dla komunikacji równorzędnej między klientami**
  -  **Port pobierania zawartości z elementu równorzędnego (HTTP/HTTPS)**

Na każdym komputerze, na którym włączono obsługę Buforowanie równorzędne Jeśli Zapora systemu Windows jest używany, Configuration Manager konfiguruje go, aby umożliwić korzystanie z portów, które można skonfigurować.

