---
title: "Obsługa funkcji systemu Windows | Dokumentacja firmy Microsoft"
description: "Dowiedz się, System Center Configuration Manager obsługuje funkcje które systemu Windows i sieci."
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0cf4bacb-6b6d-4d4f-8640-b13fe15873de
caps.latest.revision: 8
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: e040552dab21ba9a71e06a78f6acc2ffe1b0eb61
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="support-for-windows-features-and-networks-in-system-center-configuration-manager"></a>Obsługa sieci w programie System Center Configuration Manager i funkcji systemu Windows

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie opisano obsługi programu System Center Configuration Manager wspólne systemu Windows i funkcji sieci.  


##  <a name="bkmk_branchcache"></a> Usługa Usługa BranchCache  
Używając usługi Windows BranchCache z programu Configuration Manager po włączenia usługi BranchCache w punktach dystrybucji i skonfigurowanie klientów do używania usługi BranchCache w trybie rozproszonej pamięci podręcznej.

Ustawienia usługi BranchCache możesz skonfigurować w typie wdrożenia aplikacji, we wdrożeniu pakietu oraz w sekwencjach zadań.  

W przypadku spełnienia wymagań usługi BranchCache ta funkcja umożliwia klientom w lokalizacjach zdalnych uzyskanie zawartości z klientów lokalnych, które mają bieżącej pamięci podręcznej zawartości.  

Na przykład kiedy pierwszy komputer kliencki z usługą BranchCache zażąda zawartości z punktu dystrybucji skonfigurowanego jako serwer usługi BranchCache, komputer kliencki pobierze zawartość i umieści ją w pamięci podręcznej. Ta zawartość jest następnie udostępniana klientom w tej samej podsieci, który żądał tej zawartości.

Ci klienci także pamięci podręcznej zawartość. Dzięki temu kolejni klienci w tej samej podsieci nie muszą pobierać zawartości z punktu dystrybucji, a zawartość będzie rozmieszczona na wielu klientach na potrzeby przyszłych transferów.  

**Wymagania dotyczące obsługi usługi BranchCache w programie Configuration Manager:**  
-   **Skonfiguruj punkty dystrybucji:**  
    Dodaj funkcję **Usługa Windows BranchCache** na serwerze systemu lokacji, który został skonfigurowany jako punkt dystrybucji.    

    -   Punkty dystrybucji na serwerach, które są skonfigurowane do obsługi usługi BranchCache wymagają żadne dodatkowe czynności konfiguracyjne.   
    -   Nie można dodać usługi Windows BranchCache do punktu dystrybucji w chmurze, ale punkty dystrybucji w chmurze obsługują pobierania zawartości przez klientów, które są skonfigurowane dla usługi Windows BranchCache.  

-   **Konfigurowanie klientów:**    
    -   Klienci, którzy obsługują usługę BranchCache, musi być skonfigurowany dla trybu rozproszonej pamięci podręcznej usługi BranchCache.  
    -   Musi być włączona dla ustawień klienta usługi BITS ustawienia systemu operacyjnego do obsługi usługi BranchCache.   <br /> <br />
        
    Informacje dotyczące sposobu konfigurowania klientów do obsługi usługi BranchCache znajdują się w temacie [skonfigurować klientów](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache#configure-clients-for-branchcache) w sekcji [aktualizuje skonfigurować usługi BranchCache w systemie Windows 10](https://technet.microsoft.com/itpro/windows/manage/waas-branchcache).


**Program Configuration Manager obsługuje następujące systemy operacyjne klienta za pomocą usługi Windows BranchCache:**  

|System operacyjny|Szczegóły dotyczące obsługi|  
|----------------------|---------------------|  
|Windows 7 z dodatkiem SP1|Obsługa domyślna|  
|Windows 8|Obsługa domyślna|  
|Windows 8.1|Obsługa domyślna|  
|Windows 10|Obsługa domyślna|  
|Windows Server 2008 z dodatkiem SP2|**Wymaga usługi BITS 4.0**: Wersji BITS 4.0 można zainstalować na komputerach klienckich programu Configuration Manager przy użyciu dystrybucji oprogramowania lub aktualizacji oprogramowania. Aby uzyskać więcej informacji na temat usługi BITS 4.0, zobacz [Windows Management Framework](http://go.microsoft.com/fwlink/p/?LinkId=181979).<br /><br /> W tym systemie operacyjnym funkcja klienta usługi BranchCache nie jest obsługiwana na potrzeby dystrybucji oprogramowania uruchamianej z sieci ani transferów plików SMB. Ponadto ten system operacyjny nie może używać funkcji usługi BranchCache z chmurowymi punktami dystrybucji.|  
|Windows Server 2008 R2|Obsługa domyślna|  
|Windows Server 2012|Obsługa domyślna|  
|Windows Server 2012 R2|Obsługa domyślna|  

 Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [Usługa BranchCache dla systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=177945) w dokumentacji systemu Windows Server.  

##  <a name="bkmk_Workgroups"></a>Komputery w grupach roboczych  
Configuration Manager obsługuje klientów w grupach roboczych.  

-   Program Configuration Manager obsługuje przenoszenie klienta w grupie roboczej do domeny lub z domeny do grupy roboczej. Aby uzyskać więcej informacji, zobacz [jak instalować klientów programu Configuration Manager na komputerach grupy roboczej](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientWorkgroup) w [wdrażanie klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) tematu.  

> [!NOTE]  
>  Mimo że klienci w grupach roboczych są obsługiwane, wszystkie systemy lokacji muszą być członkami obsługiwanych domeny usługi Active Directory.  


##  <a name="bkmmk_datadedup"></a> Deduplikacja danych  
Program Configuration Manager obsługuje deduplikacji danych z punktów dystrybucji w następujących systemach operacyjnych:  

-   Windows Server 2012  

-   Windows Server 2012 R2  

> [!IMPORTANT]  
>  Woluminu udostępniającego pliki źródłowe pakietu nie można wybrać do deduplikacji. Jest to spowodowane deduplikacji danych używa punktów ponownej analizy, a Configuration Manager nie obsługuje korzystania z lokalizacji źródłowej zawartości z plikami, które są przechowywane na punkty ponownej analizy.  

Aby uzyskać więcej informacji, zobacz [punktów dystrybucji programu Configuration Manager i systemu Windows Server 2012 danych deduplikacji](http://blogs.technet.com/b/configmgrteam/archive/2014/02/18/configuration-manager-distribution-points-and-windows-server-2012-data-deduplication.aspx) na blogu zespołu programu Configuration Manager i [Przegląd deduplikacji danych](http://technet.microsoft.com/library/hh831602.aspx) w bibliotece TechNet serwera systemu Windows.  

##  <a name="bkmk_DA"></a> Funkcja Funkcja DirectAccess  
Program Configuration Manager obsługuje funkcji DirectAccess w systemie Windows Server 2008 R2 i nowszym w przypadku komunikacji między klientami i systemami serwera lokacji.  

-   Gdy są spełnione wszystkie wymagania dotyczące funkcji DirectAccess, funkcja DirectAccess umożliwia klientów programu Configuration Manager w Internecie, aby komunikować się z przypisanej lokacji, jak gdyby znajdowały się w sieci intranet.  

-   W przypadku akcji inicjowanych przez serwer, na przykład zdalnego sterowania lub instalacji wypychanej klienta, komputer inicjujący (na przykład serwer lokacji) musi używać protokołu IPv6, który muszą obsługiwać wszystkie pośredniczące urządzenia sieciowe.  

Menedżer konfiguracji nie obsługuje następujących za pomocą funkcji DirectAccess:  

-   Wdrażanie systemów operacyjnych  

-   Komunikacja między lokacjami programu Configuration Manager  

-   Komunikacja między serwerami systemu lokacji programu Configuration Manager w obrębie lokacji  

##  <a name="bkmk_dualboot"></a> Komputery z możliwością uruchamiania jednego z kilku systemów operacyjnych  
 Menedżer konfiguracji nie może zarządzać więcej niż jeden system operacyjny na tym samym komputerze. Jeśli istnieje więcej niż jeden system operacyjny na komputerze, który ma być zarządzany, należy dostosować metody odnajdywania i instalacji, które są używane w celu zapewnienia, że klient jest instalowany tylko na system operacyjny, który ma być zarządzany w programie Configuration Manager.  

##  <a name="bkmk_IPv6"></a>Adresy protokołu internetowego w wersji 6  
 Oprócz protokołu internetowego w wersji 4 (IPv4) programu Configuration Manager obsługuje protokołu internetowego w wersji 6 (IPv6) z następującymi wyjątkami:  

|Funkcja| Wyjątek dotyczący obsługi protokołu IPv6|  
|--------------|-------------------------------|  
|Chmurowe punkty dystrybucji|Do obsługi platformy Microsoft Azure i chmurowych punktów dystrybucji jest wymagany protokół IPv4.|  
|Urządzenia przenośne zarejestrowane przez Microsoft Intune i łącznika usługi firmy Microsoft|IPv4 jest wymagany do obsługi urządzeń przenośnych zarejestrowanych w programie Microsoft Intune i łącznika usługi firmy Microsoft.|  
|Odnajdywanie sieci|Protokół IPv4 jest wymagany po skonfigurowaniu serwera DHCP do wyszukiwania przy użyciu odnajdywania sieci.|  
|Wdrożenie systemu operacyjnego|Protokół IPv4 jest wymagany do obsługi wdrożenia systemu operacyjnego.|  
|Komunikacja serwera proxy wznawiania|Protokół IPv4 jest wymagany do obsługi pakietów serwera proxy wznawiania klienta.|  
|Windows CE|IPv4 jest wymagany do obsługi klienta programu Configuration Manager na urządzeniach z systemem Windows CE.|  

##  <a name="bkmk_NAT"></a> Translator adresów sieciowych  
 Translacji adresów sieciowych (NAT) nie jest obsługiwana w programie Configuration Manager, chyba że dana lokacja obsługuje klientów, które są połączone z Internetem i klient wykryje, że jest połączony z Internetem. Aby uzyskać więcej informacji o zarządzaniu klientami internetowymi, zobacz [Planowanie zarządzania klientami internetowymi w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-for-managing-internet-based-clients.md).  

##  <a name="bkmk_storage"></a> Specjalna technologia magazynowania  
 Menedżer konfiguracji współpracuje z żadnego sprzętu, który jest certyfikowany na liście zgodności sprzętu systemu Windows dla wersji systemu operacyjnego zainstalowanego składnika programu Configuration Manager.

Role serwera lokacji wymagają systemu plików NTFS w celu ustawienia uprawnień do katalogów i plików. Ponieważ program Configuration Manager przyjmuje, że ma ukończone własności dysku logicznego, systemów lokacji z uruchomionymi na oddzielnych komputerach nie można udostępnić logicznej partycji na dowolnej technologii. Jednak każdy komputer może używać oddzielnej partycji logicznej na tej samej partycji fizycznej udostępnionego urządzenia magazynującego.  

 **Uwagi dotyczące obsługi:**  

-   **Sieć SAN**: sieć magazynowania jest obsługiwana, gdy obsługiwany serwer z systemem Windows jest dołączony bezpośrednio do woluminu udostępnianego przez tę sieć.  

-   **Pojedyncze wystąpienie magazynu**: Programu Configuration Manager nie obsługuje konfiguracji punktu dystrybucji pakietu i podpis folderów w woluminie włączone Single Instance Storage SIS.  

     Ponadto w pamięci podręcznej klienta programu Configuration Manager nie jest obsługiwana na woluminie obsługującym usługę SIS.  

-   **Wymienny dysk**: Menedżer konfiguracji nie obsługuje instalacji systemów lokacji programu Configuration Manager lub klientów na dysku wymiennym dysku.  

