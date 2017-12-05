---
title: Nowa wersja 1710 | Dokumentacja firmy Microsoft
titleSuffix: Configuration Manager
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1710 programu System Center Configuration Manager."
ms.custom: na
ms.date: 11/20/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc6c3e5f-b9e2-400e-9d9d-446ff93c520c
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 83bd5fc972bc0bef07b206e160463db71837e827
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="what39s-new-in-version-1710-of-system-center-configuration-manager"></a>Jaki &#39; s nowego w wersji 1710 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zaktualizuj 1710 dla bieżącej gałęzi programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla zainstalowanych wcześniej lokacji, w których jest uruchomiona wersja 1610, 1702 lub 1706.

> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji bazowej programu Configuration Manager.  
>  Dowiedz się więcej o:    
>   - [Instalowanie nowej lokacji](/sccm/core/servers/deploy/install/installing-sites)  
>   - [Instalowanie aktualizacji w lokacjach](/sccm/core/servers/manage/updates)  
>   - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowych możliwości wprowadzonych w wersji 1710 programu Configuration Manager.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated features](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Version 1710 drops support for the following products:
-->


## <a name="site-infrastructure"></a>Infrastruktura lokacji

### <a name="updates-for-peer-cache-----sms500850---"></a>Aktualizacje dla równorzędnej pamięci podręcznej<!-- sms500850 -->
Począwszy od tej wersji, równorzędna pamięć podręczna nie jest już funkcji wersji wstępnej.  Żadne inne zmiany równorzędnej pamięci podręcznej zostały wprowadzone w tej wersji. Aby uzyskać więcej informacji, zobacz [buforowania równorzędnego klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache).

### <a name="cloud-distribution-point-support-for-azure-government-cloud------sms491428---"></a>Obsługa punktu dystrybucji chmury chmury Azure dla instytucji rządowych<!-- sms491428 -->
Można teraz używać [punkty dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) w chmurze Azure dla instytucji rządowych.   


<!-- ## Migration  -->


## <a name="client-management"></a>Zarządzanie klientami

### <a name="co-management-for-windows-10-devices"></a>Jednoczesne zarządzania dla urządzeń z systemem Windows 10    
<!-- 1350871 -->
Począwszy od systemu Windows 10 w wersji 1607 (znanej także jako aktualizacja rocznicy), można dołączyć urządzenie z systemem Windows 10 do lokalnej usługi Active Directory (AD) i oparta na chmurze usługi Azure AD, w tym samym czasie (rozwiązanie hybrydowe usługi Azure AD). Wspólnej zarządzania korzysta z tego ulepszenia i umożliwia jednocześnie zarządzać urządzeniami z systemem Windows 10, używając programu Configuration Manager i usługi Intune. To rozwiązanie, które zapewnia mostek z tradycyjnego zarządzania nowoczesnymi i umożliwia ścieżki do dokonania zmiany przy użyciu podejście etapowe. Aby uzyskać więcej informacji, zobacz [urządzenia zarządzania wspólnej dla systemu Windows 10](/sccm/core/clients/manage/co-management-overview).

### <a name="restart-computers-from-the-configuration-manager-console-----1356283---"></a>Uruchom ponownie komputer za pomocą konsoli programu Configuration Manager<!-- 1356283 -->
Począwszy od tej wersji, można użyć konsoli programu Configuration Manager do identyfikowania urządzenia klienckie, które wymagają ponownego uruchomienia a następnie użyć akcji powiadamiania klienta uruchomić je ponownie.

Zobacz [jak zarządzać klientami w programie System Center Configuration Manager](/sccm/core/clients/manage/manage-clients#restart-clients)


<!-- ## Compliance settings -->


## <a name="application-management"></a>Zarządzanie aplikacjami
### <a name="improvements-for-run-scripts------1236459---"></a>Ulepszenia w przypadku wykonywania skryptów<!-- 1236459 -->
Ta wersja oferuje kilka ulepszeń **uruchamianie skryptów** funkcji, która umożliwia wdrażanie skrypty programu PowerShell do uruchamiania na zarządzanych urządzeniach. Ta funkcja została wprowadzona w wersji 1706.

Ulepszenia obejmują:
- Zakresy zabezpieczeń, aby kontrolować, którzy mogą korzystać uruchamianie skryptów
- Uruchom monitorowanie skrypty w czasie rzeczywistym
- Parametry w celu wyświetlania skryptu w kreatorze tworzenia skryptu obsługi weryfikacji i są identyfikowane jako wymagane lub opcjonalne.

Aby uzyskać więcej informacji na temat uruchamiania skryptów, zobacz [tworzenia i uruchamiania skryptów](../../../apps/deploy-use/create-deploy-scripts.md).

### <a name="new-mobile-application-management-policy-settings"></a>Nowe ustawienia zasad zarządzania aplikacjami mobilnymi
<!-- 1324760 -->
Następujące ustawienia zostały dodane do ustawienia zasad zarządzania aplikacjami mobilnymi:
- **Wyłącz synchronizację kontaktów**: Aplikacja uniemożliwia zapisywania danych do aplikacji natywnej kontaktów na urządzeniu.
- **Wyłącz drukowanie**: Zapobiega aplikacji z drukowaniem pracy lub szkoły danych.

### <a name="software-center-no-longer-distorts-icons-larger-than-250x250"></a>Program Software Center nie zakłóca ikony większy niż 250 x 250  
<!-- 1356194 -->

W tej wersji programu Software Center nie będzie zakłócać ikony, które są większe niż 250 x 250. Program Software Center wprowadzone ikony wyszukiwania rozmyty. Teraz możesz ustawić ikonę z wymiarów z maksymalnie 512 x 512, i wyświetla bez zakłóceń.

Aby dodać ikony dla aplikacji w programie Software Center, zobacz [tworzenie aplikacji](/sccm/apps/deploy-use/create-applications).

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego
 > [!TIP]   
 > <!-- 1354281 -->
 > Począwszy od systemu Windows 10, wersja 1709 (znanej także jako aktualizacja twórców spadek) wersji systemu Windows nośnikami wiele wersji. Podczas konfigurowania sekwencji zadań w celu za pomocą pakietu uaktualnienia systemu operacyjnego lub obrazu systemu operacyjnego, należy wybrać [wersję, która jest obsługiwana przez program Configuration Manager](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).

### <a name="add-child-task-sequences-to-a-task-sequence"></a>Dodaj do sekwencji zadań sekwencje zadań podrzędnych
<!-- 1261338 -->

Możesz dodać nowy krok sekwencji zadań uruchamiana innej sekwencji zadań, która tworzy relacji nadrzędny/podrzędny między sekwencji zadań. Dzięki temu można utworzyć więcej sekwencje zadań moduły, które można użyć ponownie.  

Aby dowiedzieć się więcej o sekwencji zadań podrzędnych, zobacz [sekwencji zadań podrzędnych](/sccm/osd/understand/task-sequence-steps#child-task-sequence).

## <a name="software-center-customization"></a>Dostosowywanie Centrum oprogramowania
<!-- 1351224 -->
Można dodać znakowanie elementów przedsiębiorstwa i określ widoczność karty w Centrum oprogramowania. Można dodać nazwę firmy określonego programu Software Center, ustawić motyw kolorów konfiguracji programu Software Center, ustawienie logo firmy i ustawienie kartach widoczny na urządzeniach klienckich.

Aby uzyskać więcej informacji, zobacz [Planowanie konfiguracji zarządzania aplikacjami w programie System Center Configuration Manager i przeprowadzanie konfiguracji](/sccm/apps/plan-design/plan-for-and-configure-application-management).

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="surface-driver-updates-----1098490---"></a>Aktualizacje sterowników powierzchni<!-- 1098490 -->
Począwszy od tej wersji, zarządzanie aktualizacjami powierzchni sterownik nie jest już funkcji wersji wstępnej.  


## <a name="reporting"></a>Raportowanie

### <a name="limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health"></a>Ogranicz rozszerzony systemu Windows 10 telemetrię, aby wysyłać dane tylko istotne dla kondycji urządzenia Analytics systemu Windows
<!-- 1356148 -->

Można teraz ustawić zbieranie danych telemetrii systemu Windows 10 poziom **rozszerzony (ograniczony)**. To ustawienie umożliwia uzyskania przydatnych wyników informacje na temat urządzeń w środowisku bez urządzenia podlegające wszystkie dane w **rozszerzony** telemetrii poziomu z systemem Windows 10 w wersji 1709 lub nowszej.

Aby uzyskać więcej informacji, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](/sccm/core/clients/deploy/configure-client-settings).

<!-- ## Inventory  -->


## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi

### <a name="actions-for-non-compliance"></a>Akcje dla braku zgodności 
<!--1321366 -->    
Można teraz skonfigurować uporządkowane czasu sekwencję akcji, które są stosowane do urządzeń, które stwierdzona zostanie niezgodność. Na przykład można powiadamiać użytkowników o niezgodnych urządzeń za pośrednictwem poczty e-mail lub oznaczyć te urządzenia niezgodne. Aby uzyskać więcej informacji, zobacz [ustawiania akcji dla zgodności z systemem innym niż](/sccm/mdm/deploy-use/actions-for-noncompliance).

### <a name="windows-10-arm64-device-support"></a>Obsługa urządzeń z systemem Windows 10 ARM64
<!-- 1355000 -->

Scenariuszy zarządzania urządzeniami Przenośnymi urządzeniami przenośnymi hybrydowego będą obsługiwane na urządzeniach ARM64 z systemem Windows 10, jeśli te urządzenia nie są dostępne.

Te scenariusze obejmują:

- [Rejestrowanie urządzeń](../../../mdm/deploy-use/enroll-hybrid-windows.md)
- [Akcje pełnego i selektywnego czyszczenia danych](../../../mdm/deploy-use/wipe-lock-reset-devices.md)
- [Zarządzanie ustawieniami za pomocą elementów konfiguracji i linii bazowych](../../../mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Zarządzanie zasadami zgodności](../../../mdm/deploy-use/device-compliance-policies.md)
- Zarządzanie dostępem do zasobów firmy za pomocą:
   - [Profile certyfikatów](../../../mdm/deploy-use/create-pfx-certificate-profiles.md)
   - [Profile sieci VPN](../../../mdm/deploy-use/create-vpn-profiles.md)
   - [Profile sieci Wi-Fi](../../../mdm/deploy-use/create-wifi-profiles.md)
   - [Profile poczty e-mail](../../../mdm/deploy-use/create-exchange-activesync-profiles.md)
- [Konfigurowanie usługi Windows Hello dla firm zasady](../../../mdm/deploy-use/windows-hello-for-business-settings.md)
- [Zarządzanie aplikacjami](../../../mdm/deploy-use/management-tasks-applications.md)

### <a name="improved-vpn-profile-experience-in-configuration-manager-console"></a>VPN udoskonalone środowisko profilu w konsoli programu Configuration Manager 
<!-- 1318232 -->

W tej wersji Zaktualizowaliśmy VPN profilu Kreatora właściwości strony i aby wyświetlić ustawienia odpowiednie dla wybranej platformy:


- Dotyczy wszystkich platform własną przepływu pracy, co oznacza, że nowych profilów sieci VPN zawiera tylko ustawienia, które są obsługiwane przez platformę.
- **Obsługiwane platformy** pojawia się po stronie **ogólne** strony.  Możesz teraz wybrać platformę przed ustawieniem wartości właściwości.
- Gdy ma wartość platformy **Android**, **Android for Work**, lub **Windows Phone 8.1**, **obsługiwane platformy** strona nie jest wymagana i jest nie są wyświetlane.
- Przepływ pracy oparty na klienta programu Configuration Manager została połączona z hybrydowego urządzeniami przenośnymi (MDM) opartego na kliencie systemu Windows 10 przepływy pracy; obsługują one tych samych ustawień.
- Każda platforma przepływ pracy zawiera tylko ustawienia odpowiednie dla tego przepływu pracy.  Na przykład Android przepływ pracy zawiera ustawienia właściwe dla systemu Android; Ustawienia właściwe dla systemu iOS lub Windows 10 Mobile są już wyświetlane w przepływie pracy z systemem Android.
- Dla urządzeń Windows 8.1, typy połączeń zarządzanych przez klienta programu Configuration Manager tylko (nieobsługiwane przez usługę Intune) wyraźnie są oznaczone.
- Na stronie automatyczne połączenie VPN jest przestarzały i został usunięty.

Te zmiany dotyczą nowych profilów sieci VPN.  

Aby zminimalizować ryzyko zgodności, istniejących profilów sieci VPN nie uległy zmianie.  Podczas edycji istniejącego profilu, ustawienia, są tak samo, jak podczas tworzenia profilu.  

Aby uzyskać więcej informacji, zobacz [profilów sieci VPN na urządzeniach przenośnych w programie System Center Configuration Manager](../../../mdm/deploy-use/create-vpn-profiles.md).

### <a name="limited-support-for-cryptography-next-generation-cng-certificates----1356191---"></a>Ograniczona obsługa szyfrowania: Next Generation (CNG) certyfikatów<!-- 1356191 -->

Menedżer konfiguracji ma ograniczoną obsługę szyfrowania: Certyfikaty następnej generacji (CNG). Klienci programu Configuration Manager mogą używać certyfikatu uwierzytelniania klienta PKI z kluczem prywatnym w dostawcy magazynu kluczy CNG (KSP). Dostawcy magazynu KLUCZY, z obsługą klientów programu Configuration Manager obsługuje oparte na sprzęcie klucza prywatnego, takich jak moduł TPM dostawcy magazynu KLUCZY dla certyfikatów uwierzytelniania klienta PKI.

Aby uzyskać więcej informacji, zobacz [Omówienie certyfikatów CNG](../network/cng-certificates-overview.md).

## <a name="protect-devices"></a>Ochrona urządzeń

### <a name="create-and-deploy-exploit-guard-policies"></a>Tworzenie i wdrażanie zasad wykorzystać zabezpieczenia
<!-- 1355468 -->

Możesz [tworzenie i wdrażanie zasad](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) który zarządzania wszystkie cztery składniki systemu Windows Defender wykorzystać osłony, w tym zmniejszenie powierzchni ataku, folder z kontrolą dostępu, ochrony wykorzystać i ochrony sieci.

### <a name="create-and-deploy-windows-defender-application-guard-policy"></a>Tworzenie i wdrażanie zasad Guard aplikacji programu Windows Defender
<!-- 1351960 -->

Możesz [tworzenie i wdrażanie zasad systemu Windows Defender aplikacji Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy) przy użyciu Menedżera konfiguracji programu endpoint protection.

### <a name="device-guard-policy-changes"></a>Zmiany zasad ochrona urządzeń
<!-- 1355092 -->
Trzy następujące zmiany wprowadzono w odniesieniu do zasady ochrony urządzeń:

- Zmieniono zasady ochrona urządzeń zasad kontroli aplikacji Defender systemu Windows. Tak, na przykład **Kreatora zasad ochrony urządzeń Utwórz** ma teraz nazwę **Kreatora zasad tworzenia kontrolki aplikacji systemu Windows Defender**.
- Urządzeń przy użyciu spadek twórców aktualizacji dla systemu Windows wersja 1709 nie wymagają ponownego uruchomienia w celu stosowania zasad formant programu Windows Defender aplikacji. Ponowne uruchomienie jest nadal domyślnie, ale można [wyłączyć ponownego uruchomienia](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager).
- Możesz [Ustaw urządzenia do automatycznego uruchamiania oprogramowania](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager) ufa inteligentnego wykres zabezpieczeń.





## <a name="next-steps"></a>Następne kroki
Po Twoje gotowe do zainstalowania tej wersji, zobacz [aktualizacje programu Configuration Manager](/sccm/core/servers/manage/updates).
