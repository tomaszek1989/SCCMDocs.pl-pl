---
title: "Obsługa funkcji systemu Windows"
titleSuffix: Configuration Manager
description: "Dowiedz się, które systemu Windows i sieci programu System Center Configuration Manager obsługuje funkcje."
ms.custom: na
ms.date: 8/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: "8"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 0cc1915a73ed55403eca27021b77aab1fd1ddb03
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>Obsługa funkcji systemu Windows i sieci w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera informacje pomocy technicznej programu System Center Configuration Manager wspólne systemu Windows i funkcji sieciowych.  


##  <a name="bkmk_branchcache"></a> Usługa Usługa BranchCache  
Używając usługi Windows BranchCache z programem Configuration Manager w przypadku włączenia usługi BranchCache w punktach dystrybucji i skonfiguruj klientów do używania usługi BranchCache w trybie rozproszonej pamięci podręcznej.

Ustawienia usługi BranchCache możesz skonfigurować w typie wdrożenia aplikacji, we wdrożeniu pakietu oraz w sekwencjach zadań.  

Gdy są spełnione wymagania dotyczące usługi BranchCache, ta funkcja umożliwia klientom w lokalizacjach zdalnych pobieranie zawartości z lokalnych klientów, którzy mają bieżącej pamięci podręcznej zawartości.  

Na przykład kiedy pierwszy komputer kliencki z usługą BranchCache zażąda zawartości z punktu dystrybucji skonfigurowanego jako serwer usługi BranchCache, komputer kliencki pobierze zawartość i umieści ją w pamięci podręcznej. Tej zawartości jest następnie udostępniana klientom w tej samej podsieci, którego żąda ta zawartość.

Ci klienci także pamięci podręcznej zawartości. Dzięki temu kolejni klienci w tej samej podsieci nie muszą pobierać zawartości z punktu dystrybucji, a zawartość będzie rozmieszczona na wielu klientach na potrzeby przyszłych transferów.  

**Wymagania dotyczące obsługi usługi BranchCache w programie Configuration Manager:**  
-   **Konfigurowanie punktów dystrybucji:**  
    Dodaj funkcję **Usługa Windows BranchCache** na serwerze systemu lokacji, który został skonfigurowany jako punkt dystrybucji.    

    -   Punkty dystrybucji na serwerach, które są skonfigurowane do obsługi usługi BranchCache nie wymagają dodatkowej konfiguracji.   
    -   Nie można dodać usługi Windows BranchCache do punktu dystrybucji w chmurze, ale punkty chmurowych punktów dystrybucji obsługują pobieranie zawartości przez klientów, które są skonfigurowane dla usługi Windows BranchCache.  

-   **Konfigurowanie klientów:**    
    -   Klienci, którzy mogą obsługiwać usługę BranchCache, musi być skonfigurowany dla trybu rozproszonej pamięci podręcznej usługi BranchCache.  
    -   Ustawienia systemu operacyjnego dla ustawień klienta usługi BITS musi być włączony do obsługi usługi BranchCache.   <br /> <br />

    Aby uzyskać informacje dotyczące sposobu konfigurowania klientów do obsługi usługi BranchCache, zobacz [skonfigurować klientów](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache#configure-clients-for-branchcache) sekcji [aktualizuje konfigurowania usługi BranchCache dla systemu Windows 10](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache).


**Program Configuration Manager obsługuje następujące systemy operacyjne klienta Windows BranchCache:**  

|System operacyjny|Szczegóły dotyczące obsługi|  
|----------------------|---------------------|  
|Windows 7 z dodatkiem SP1|Obsługa domyślna|  
|Windows 8|Obsługa domyślna|  
|Windows 8.1|Obsługa domyślna|  
|Windows 10|Obsługa domyślna|  
|Windows Server 2008 z dodatkiem SP2|**Wymaga usługi BITS 4.0**: Usługi BITS 4.0 na klientach programu Configuration Manager można zainstalować za pomocą aktualizacji oprogramowania lub dystrybucji oprogramowania. Aby uzyskać więcej informacji na temat usługi BITS 4.0, zobacz [Windows Management Framework](http://go.microsoft.com/fwlink/p/?LinkId=181979).<br /><br /> W tym systemie operacyjnym funkcja klienta usługi BranchCache nie jest obsługiwana na potrzeby dystrybucji oprogramowania uruchamianej z sieci ani transferów plików SMB. Ponadto ten system operacyjny nie może używać funkcji usługi BranchCache z chmurowymi punktami dystrybucji.|  
|Windows Server 2008 R2|Obsługa domyślna|  
|Windows Server 2012|Obsługa domyślna|  
|Windows Server 2012 R2|Obsługa domyślna|  

 Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [Usługa BranchCache dla systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=177945) w dokumentacji systemu Windows Server.  

##  <a name="bkmk_Workgroups"></a>Komputery w grupach roboczych  
Configuration Manager obsługuje klientów w grupach roboczych.  

-   Program Configuration Manager obsługuje przenoszenie klienta z grupy roboczej do domeny albo z domeny do grupy roboczej. Aby uzyskać więcej informacji, zobacz [jak instalować klientów programu Configuration Manager na komputerach grupy roboczej](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup) w [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) tematu.  

> [!NOTE]  
>  Mimo że klienci w grupach roboczych są obsługiwani, wszystkie systemy lokacji muszą być elementami członkowskimi obsługiwanej domeny usługi Active Directory.  


##  <a name="bkmmk_datadedup"></a> Deduplikacja danych  
Program Configuration Manager obsługuje używanie deduplikacji danych dla punktów dystrybucji w następujących systemach operacyjnych:  

-   Windows Server 2016
-   Windows Server 2012 R2  
-   Windows Server 2012  



> [!IMPORTANT]  
>  Woluminu udostępniającego pliki źródłowe pakietu nie można wybrać do deduplikacji. Jest tak, ponieważ funkcja deduplikacji danych używa punktów ponownej analizy, a Configuration Manager nie obsługuje używania lokalizacji źródła zawartości z plikami przechowywanymi w punktach ponownej analizy.  

Aby uzyskać więcej informacji, zobacz [punkty dystrybucji programu Configuration Manager i Deduplikacja danych w systemie Windows Server 2012](http://blogs.technet.com/b/configmgrteam/archive/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication.aspx) w blogu zespołu programu Configuration Manager i [omówienie deduplikacji danych](http://technet.microsoft.com/library/hh831602.aspx) w bibliotece TechNet systemu Windows Server.  

##  <a name="bkmk_DA"></a> Funkcja Funkcja DirectAccess  
Program Configuration Manager obsługuje funkcję DirectAccess w systemie Windows Server 2008 R2 i nowszym w przypadku komunikacji między klientami i systemami serwera lokacji.  

-   Gdy są spełnione wszystkie wymagania dotyczące funkcji DirectAccess, funkcja DirectAccess umożliwia klientów programu Configuration Manager w Internecie, aby komunikować się z przypisanej lokacji, jak gdyby znajdowały się w sieci intranet.  

-   W przypadku akcji inicjowanych przez serwer, na przykład zdalnego sterowania lub instalacji wypychanej klienta, komputer inicjujący (na przykład serwer lokacji) musi używać protokołu IPv6, który muszą obsługiwać wszystkie pośredniczące urządzenia sieciowe.  

Program Configuration Manager nie obsługuje następujących za pośrednictwem funkcji DirectAccess:  

-   Wdrażanie systemów operacyjnych  

-   Komunikacja między lokacjami programu Configuration Manager  

-   Komunikacja między serwerami systemu lokacji programu Configuration Manager w obrębie lokacji  

##  <a name="bkmk_dualboot"></a> Komputery z możliwością uruchamiania jednego z kilku systemów operacyjnych  
 Menedżer konfiguracji nie może zarządzać więcej niż jeden system operacyjny na jednym komputerze. Jeśli istnieje więcej niż jeden system operacyjny na komputerze, który ma być zarządzany, Dostosuj metody odnajdywania i instalacji, które są używane do zapewnienia, że klient jest zainstalowany tylko w systemie operacyjnym, który ma być zarządzany w programie Configuration Manager.  

##  <a name="bkmk_IPv6"></a>Internet Protocol w wersji 6  
 Oprócz Internet Protocol w wersji 4 (IPv4) program Configuration Manager obsługuje Internet Protocol w wersji 6 (IPv6) z następującymi wyjątkami:  

|Funkcja| Wyjątek dotyczący obsługi protokołu IPv6|  
|--------------|-------------------------------|  
|Chmurowe punkty dystrybucji|Do obsługi platformy Microsoft Azure i chmurowych punktów dystrybucji jest wymagany protokół IPv4.|  
|Urządzenia przenośne zarejestrowane przez program Microsoft Intune i łącznik usługi firmy Microsoft|Protokół IPv4 jest wymagany do obsługi urządzeń przenośnych zarejestrowanych przez program Microsoft Intune i łącznik usługi firmy Microsoft.|  
|Odnajdywanie sieci|Protokół IPv4 jest wymagany po skonfigurowaniu serwera DHCP do wyszukiwania przy użyciu odnajdywania sieci.|  
|Wdrożenie systemu operacyjnego|Protokół IPv4 jest wymagany do obsługi wdrożenia systemu operacyjnego.|  
|Komunikacja serwera proxy wznawiania|Protokół IPv4 jest wymagany do obsługi pakietów serwera proxy wznawiania klienta.|  
|Windows CE|Protokół IPv4 jest wymagany do obsługi klienta programu Configuration Manager na urządzeniach z systemem Windows CE.|  

##  <a name="bkmk_NAT"></a> Translator adresów sieciowych  
 Translatora adresów sieciowych (NAT) nie jest obsługiwana w programie Configuration Manager, chyba że lokacja obsługuje klientów znajdujących się w Internecie i klient wykryje, że jest połączony z Internetem. Aby uzyskać więcej informacji dotyczących zarządzania klientami internetowymi, zobacz [Planowanie zarządzania klientami internetowymi w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md).  

##  <a name="bkmk_storage"></a> Specjalna technologia magazynowania  
 Programu Configuration Manager działa z dowolnym certyfikowanym sprzętem znajdującym się na liście zgodności sprzętu wersji systemu operacyjnego zainstalowanego składnika programu Configuration Manager systemu Windows.

Role serwera lokacji wymagają systemu plików NTFS w celu ustawienia uprawnień do katalogów i plików. Ponieważ programu Configuration Manager przyjęto założenie, że ma całkowitą własność dysku logicznego, systemy lokacji działające na oddzielnych komputerach nie można udostępnić partycji logicznej przy użyciu żadnej technologii magazynowania. Jednak każdy komputer może używać oddzielnej partycji logicznej na tej samej partycji fizycznej udostępnionego urządzenia magazynującego.  

 **Uwagi dotyczące obsługi:**  

-   **Sieć SAN**: sieć magazynowania jest obsługiwana, gdy obsługiwany serwer z systemem Windows jest dołączony bezpośrednio do woluminu udostępnianego przez tę sieć.  

-   **Single Instance Storage**: Programu Configuration Manager nie obsługuje konfiguracji punktu dystrybucji pakietu i podpis folderów w woluminie włączone Single Instance Storage SIS.  

     Ponadto w pamięci podręcznej klienta programu Configuration Manager nie jest obsługiwana na woluminie obsługującym usługę SIS.  

-   **Dysk wymienny**: Menedżer konfiguracji nie obsługuje instalacji klientów lub systemy lokacji programu Configuration Manager na dysku wymiennym.  
