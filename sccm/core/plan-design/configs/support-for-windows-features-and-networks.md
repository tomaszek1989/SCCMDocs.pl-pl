---
title: Obsługa funkcji systemu Windows
titleSuffix: Configuration Manager
description: Dowiedz się, które systemu Windows i sieci programu System Center Configuration Manager obsługuje funkcje.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 4a41efa9b4c33a77d6aa2fa9e806e24ae33cc330
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>Obsługa funkcji systemu Windows i sieci w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule identyfikuje pomocy technicznej programu Configuration Manager wspólne systemu Windows i funkcji sieciowych.  


##  <a name="bkmk_branchcache"></a> Usługa Usługa BranchCache  
Użyciem usługi Windows BranchCache z programem Configuration Manager możesz ją włączyć w punktach dystrybucji i skonfiguruj klientów do używania go w trybie rozproszonej pamięci podręcznej.

Ustawienia usługi BranchCache możesz skonfigurować w typie wdrożenia aplikacji, we wdrożeniu pakietu oraz w sekwencjach zadań.  

Gdy są spełnione wymagania dotyczące usługi BranchCache, ta funkcja umożliwia klientom w lokalizacjach zdalnych pobieranie zawartości z lokalnych klientów, którzy mają bieżącej pamięci podręcznej zawartości.  

Na przykład gdy pierwszy klient z włączoną usługą BranchCache zażąda zawartości z punktu dystrybucji, który jest skonfigurowany jako serwer usługi BranchCache, klient pobierze i buforuje zawartość. Tej zawartości jest następnie udostępniana klientom w tej samej podsieci, którego żąda ta zawartość.

Ci klienci także pamięci podręcznej zawartości. Innym klientom w tej samej podsieci nie trzeba pobierać zawartość z punktu dystrybucji. Zawartość będzie rozmieszczona na wielu klientach na potrzeby przyszłych transferów.  

### <a name="requirements-to-support-branchcache-with-configuration-manager"></a>Wymagania dotyczące obsługi usługi BranchCache w programie Configuration Manager
-   **Konfigurowanie punktów dystrybucji**: Dodaj **usługi Windows BranchCache** funkcji na serwerze systemu lokacji, który jest skonfigurowany jako punkt dystrybucji.    
    -   Punkty dystrybucji na serwerach, które są skonfigurowane do obsługi usługi BranchCache nie wymagają dodatkowej konfiguracji.   
    -   Nie można dodać usługi Windows BranchCache do punktu dystrybucji w chmurze. Punkty chmurowych punktów dystrybucji obsługują pobieranie zawartości przez klientów, które są skonfigurowane dla usługi Windows BranchCache.  

-   **Konfigurowanie klientów**:    
    -   Klienci, którzy mogą obsługiwać usługę BranchCache, musi być skonfigurowany dla trybu rozproszonej pamięci podręcznej usługi BranchCache.  
    -   Ustawienia systemu operacyjnego dla ustawień klienta usługi BITS musi być włączony do obsługi usługi BranchCache.   <br /> <br />

    Aby uzyskać informacje, zobacz [skonfigurować klientów usługi BranchCache](https://docs.microsoft.com/windows/deployment/update/waas-branchcache#configure-clients-for-branchcache) w dokumentacji systemu Windows.


### <a name="configuration-manager-supported-os-versions-with-windows-branchcache"></a>Menedżer konfiguracji obsługiwane wersje systemu operacyjnego Windows BranchCache

|System operacyjny|Szczegóły dotyczące obsługi|  
|----------------------|---------------------|  
|Windows 7 z dodatkiem SP1|Obsługa domyślna|  
|Windows 8|Obsługa domyślna|  
|Windows 8.1|Obsługa domyślna|  
|Windows 10|Obsługa domyślna|  
|Windows Server 2008 z dodatkiem SP2|**Wymaga usługi BITS 4.0**: Usługi BITS 4.0 na klientach programu Configuration Manager można zainstalować za pomocą aktualizacji oprogramowania lub dystrybucji oprogramowania. Aby uzyskać więcej informacji, zobacz [Windows Management Framework](https://support.microsoft.com/help/968929/windows-management-framework-windows-powershell-2-0-winrm-2-0-and-bits).<br /><br /> W tym systemie operacyjnym funkcja klienta usługi BranchCache nie jest obsługiwane dla dystrybucji oprogramowania, który jest uruchamiany z sieci ani transferów plików SMB. Ponadto ten system operacyjny nie może używać funkcji usługi BranchCache z chmurowymi punktami dystrybucji.|  
|Windows Server 2008 R2|Obsługa domyślna|  
|Windows Server 2012|Obsługa domyślna|  
|Windows Server 2012 R2|Obsługa domyślna|  
|Windows Server 2016|Obsługa domyślna|  

 Aby uzyskać więcej informacji, zobacz [usługi BranchCache dla systemu Windows](https://docs.microsoft.com/windows-server/networking/branchcache/branchcache) w dokumentacji systemu Windows Server.  



##  <a name="bkmk_Workgroups"></a> Komputery w grupach roboczych  
Configuration Manager obsługuje klientów w grupach roboczych.  

-   Program Configuration Manager obsługuje przenoszenie klienta z grupy roboczej do domeny albo z domeny do grupy roboczej. Aby uzyskać więcej informacji, zobacz [jak instalować klientów programu Configuration Manager na komputerach grupy roboczej](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup) w [jak wdrożyć klientów na komputerach z systemem Windows](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) tematu.  

> [!NOTE]  
>  Mimo że klienci w grupach roboczych są obsługiwani, wszystkie systemy lokacji muszą być elementami członkowskimi obsługiwanej domeny usługi Active Directory.  



##  <a name="bkmmk_datadedup"></a> Deduplikacja danych  
Program Configuration Manager obsługuje używanie deduplikacji danych dla punktów dystrybucji w następujących systemach operacyjnych:  

-   Windows Server 2016
-   Windows Server 2012 R2  
-   Windows Server 2012  


> [!IMPORTANT]  
>  Woluminu udostępniającego pliki źródłowe pakietu nie można wybrać do deduplikacji. To ograniczenie dotyczy, ponieważ deduplikacja danych używa punktów ponownej analizy. Menedżer konfiguracji nie obsługuje używania lokalizacji źródła zawartości z plikami przechowywanymi w punktach ponownej analizy.  

Aby uzyskać więcej informacji, zobacz [punkty dystrybucji programu Configuration Manager i Deduplikacja danych w systemie Windows Server 2012](https://cloudblogs.microsoft.com/enterprisemobility/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication/) w blogu zespołu programu Configuration Manager i [omówienie deduplikacji danych](https://docs.microsoft.com/windows-server/storage/data-deduplication/overview) w Dokumentacja systemu Windows Server.  



##  <a name="bkmk_DA"></a> Funkcja Funkcja DirectAccess  
Program Configuration Manager obsługuje funkcję DirectAccess do komunikacji między klientami i systemami serwera lokacji.  

-   Gdy są spełnione wszystkie wymagania dotyczące funkcji DirectAccess, umożliwia klientów programu Configuration Manager w Internecie, aby komunikować się z przypisanej lokacji, jak gdyby znajdowały się w sieci intranet.  

-   Akcje inicjowanych przez serwer, na przykład zdalnego sterowania lub instalacji wypychanej klienta komputer inicjujący musi być uruchomiona IPv6. Wszystkie pośredniczące urządzenia sieciowe muszą obsługiwać tego protokołu.  

Program Configuration Manager nie obsługuje następujące funkcje za pośrednictwem funkcji DirectAccess:  

-   Wdrażanie systemów operacyjnych  

-   Komunikacja między lokacjami programu Configuration Manager  

-   Komunikacja między serwerami systemu lokacji programu Configuration Manager w obrębie lokacji  



##  <a name="bkmk_dualboot"></a> Komputery z możliwością uruchamiania jednego z kilku systemów operacyjnych  
 Menedżer konfiguracji nie może zarządzać więcej niż jeden system operacyjny na jednym komputerze. Jeśli istnieje więcej niż jeden system operacyjny na komputerze do zarządzania, Dostosuj odnajdowania lokacji i metody instalacji klienta, aby upewnić się, że klient jest zainstalowany tylko w systemie operacyjnym, który ma być zarządzany w programie Configuration Manager.  



##  <a name="bkmk_IPv6"></a> Internet Protocol w wersji 6  
 Oprócz Internet Protocol w wersji 4 (IPv4) program Configuration Manager obsługuje Internet Protocol w wersji 6 (IPv6) z następującymi wyjątkami:  

|Funkcja| Wyjątek dotyczący obsługi protokołu IPv6|  
|--------------|-------------------------------|  
|Chmurowe punkty dystrybucji|Do obsługi platformy Microsoft Azure i chmurowych punktów dystrybucji jest wymagany protokół IPv4.|  
|Brama zarządzania w chmurze|Protokół IPv4 jest wymagany do obsługi programu Microsoft Azure i brama zarządzania chmury.|  
|Urządzenia przenośne zarejestrowane przez program Microsoft Intune i łącznik usługi firmy Microsoft|Protokół IPv4 jest wymagany do obsługi urządzeń przenośnych zarejestrowanych przez program Microsoft Intune i łącznik usługi firmy Microsoft.|  
|Odnajdywanie sieci|Protokół IPv4 jest wymagany po skonfigurowaniu serwera DHCP do wyszukiwania przy użyciu odnajdywania sieci.|  
|Wdrażanie systemu operacyjnego|Protokół IPv4 jest wymagany do obsługi wdrożenia systemu operacyjnego. |  
|Komunikacja serwera proxy wznawiania|Protokół IPv4 jest wymagany do obsługi pakietów serwera proxy wznawiania klienta.|  
|Windows CE|Protokół IPv4 jest wymagany do obsługi klienta programu Configuration Manager na urządzeniach z systemem Windows CE.|  



##  <a name="bkmk_NAT"></a> Translator adresów sieciowych  
 Translatora adresów sieciowych (NAT) nie jest obsługiwana w programie Configuration Manager, chyba że lokacja obsługuje klientów znajdujących się w Internecie i klient wykryje, że jest połączony z Internetem. Aby uzyskać więcej informacji dotyczących zarządzania klientami internetowymi, zobacz [Planowanie zarządzania klientami internetowymi](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md).  



##  <a name="bkmk_storage"></a> Specjalna technologia magazynowania  
 Programu Configuration Manager działa z dowolnym certyfikowanym sprzętem znajdującym się na liście zgodności sprzętu wersji systemu operacyjnego zainstalowanego składnika programu Configuration Manager systemu Windows.

Role serwera lokacji wymagają systemu plików NTFS, program Configuration Manager można ustawić uprawnienia plików i katalogów. Menedżer konfiguracji przyjęto założenie, że ma całkowitą własność dysku logicznego. Systemy lokacji działające na oddzielnych komputerach nie można udostępnić partycji logicznej przy użyciu żadnej technologii magazynowania. Jednak każdy komputer może używać oddzielnej partycji logicznej na tej samej partycji fizycznej udostępnionego urządzenia magazynującego.  

 ### <a name="support-considerations"></a>Uwagi dotyczące obsługi

-   **Sieć SAN**: sieć magazynowania jest obsługiwana, gdy obsługiwany serwer z systemem Windows jest dołączony bezpośrednio do woluminu udostępnianego przez tę sieć.  

-   **Single Instance Storage**: Programu Configuration Manager nie obsługuje konfiguracji punktu dystrybucji pakietu i podpis folderów w woluminie włączone Single Instance Storage SIS.  

     Ponadto w pamięci podręcznej klienta programu Configuration Manager nie jest obsługiwana na woluminie obsługującym usługę SIS.  

-   **Dysk wymienny**: Menedżer konfiguracji nie obsługuje instalacji klientów lub systemy lokacji programu Configuration Manager na dysku wymiennym.  
