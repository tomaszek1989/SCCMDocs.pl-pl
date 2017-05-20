---
title: "Buforowanie równorzędne systemu Windows PE, aby zmniejszyć ruch w sieci WAN przygotować | Dokumentacja firmy Microsoft"
description: "Buforowanie równorzędne systemu Windows PE działa w środowisku Windows PE na pobieranie zawartości z lokalnego elementu równorzędnego i zminimalizować ruch w sieci WAN, gdy jest żaden lokalny punkt dystrybucji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 6c64f276-b88c-4b1e-8073-331876a03038
caps.latest.revision: 11
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 814c6133a30b1116d05aaeafddb0dfb7fe2a390e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-windows-pe-peer-cache-to-reduce-wan-traffic-in-system-center-configuration-manager"></a>Przygotowywanie równorzędnej pamięci podręcznej systemu Windows PE w celu zredukowania ruchu w sieci WAN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Podczas wdrażania nowego systemu operacyjnego w programie System Center Configuration Manager komputerów korzystających z sekwencji zadań umożliwia Buforowanie równorzędne systemu Windows PE pobierania zawartości z lokalnego równorzędnych (peer źródła pamięci podręcznej) zamiast pobierać zawartość z punktu dystrybucji. Minimalizuje to ruch w sieci rozległej w scenariuszach oddziału firmy bez lokalnego punktu dystrybucji.  

 Buforowanie równorzędne systemu Windows PE jest podobny do [usługi Windows BranchCache](http://technet.microsoft.com/library/mt617255\(TechNet.10\).aspx#bkmk_branchcache), ale funkcje w środowisku preinstalacji systemu Windows (Windows PE). W przypadku uruchomienia sekwencji zadań w kontekście systemu operacyjnego, na przykład z poziomu programu Software Center na kliencie, równorzędna pamięć podręczna systemu Windows PE nie jest używana. Poniższe terminy są używane do opisywania klientów korzystających z równorzędnej pamięci podręcznej systemu Windows PE:  

-   **Klient równorzędnej pamięci podręcznej** to komputer skonfigurowany do używania równorzędnej pamięci podręcznej systemu Windows PE.  

-   **Źródło równorzędnej pamięci podręcznej** to klient skonfigurowany na potrzeby zapewniania równorzędnej pamięci podręcznej, który udostępnia zawartość innym klientom równorzędnej pamięci podręcznej żądającym tej zawartości.  

Umożliwia zarządzanie Buforowanie równorzędne w poniższych sekcjach.

##  <a name="BKMK_PeerCacheObjects"></a> Obiekty przechowywane w źródle równorzędnej pamięci podręcznej  
 Sekwencja zadań skonfigurowana do korzystania z równorzędnej pamięci podręcznej systemu Windows PE może uzyskać następujące obiekty zawartości podczas pracy w systemie Windows PE:  

-   Obraz systemu operacyjnego  

-   Pakiety sterowników  

-   Pakiety i programy (Jeśli klient w dalszym ciągu do uruchomienia sekwencji zadań w pełnej wersji systemu operacyjnego, klient pobiera tę zawartość z pamięci podręcznej źródła równorzędnego Jeśli sekwencja zadań pierwotnie został skonfigurowany dla Buforowanie równorzędne podczas uruchamiania w środowisku Windows PE.)  

-   Dodatkowe obrazy rozruchowe  

 Następujące obiekty zawartości nigdy nie są przesyłane przy użyciu równorzędnej pamięci podręcznej. Zamiast tego są przesyłane z punktu dystrybucji lub za pomocą usługi Windows BranchCache, jeśli w środowisku skonfigurowano tę usługę:  

-   Aplikacje  

-   Aktualizacje oprogramowania  

##  <a name="BKMK_PeerCacheWork"></a> Jak działa równorzędna pamięć podręczna systemu Windows PE?  
 Rozważmy scenariusz biura oddziału bez punktu dystrybucji, ale z włączoną obsługą równorzędnej pamięci podręcznej systemu Windows PE na kilku klientach. Sekwencja zadań skonfigurowana do korzystania z równorzędnej pamięci podręcznej jest wdrażana na kilku klientach skonfigurowanych jako część źródła równorzędnej pamięci podręcznej. Pierwszy klient, na którym uruchomiono sekwencję zadań, emituje żądanie w poszukiwaniu elementu równorzędnego z zawartością. Nie znajduje takiego elementu, więc pobiera zawartość z punktu dystrybucji w sieci WAN. Klient instaluje nowy obraz, a następnie przechowuje zawartość w pamięci podręcznej klienta programu Configuration Manager, może być traktowane jako źródło elementów równorzędnych pamięci podręcznej innym klientom. Po uruchomieniu przez następnego klienta sekwencji zadań klient ten emituje żądanie w podsieci dotyczące źródła równorzędnej pamięci podręcznej. Odpowiada pierwszy klient i udostępnia zawartość znajdującą się w jego pamięci podrzędnej.  

##  <a name="BKMK_PeerCacheDetermine"></a> Określanie, którzy klienci będą częścią źródła równorzędnej pamięci podręcznej systemu Windows PE  
 Aby ułatwić określenie, które komputery wybrać jako źródło równorzędnej pamięci podręcznej systemu Windows PE, należy wziąć pod uwagę kilka kwestii:  

-   Źródło równorzędnej pamięci podręcznej systemu Windows PE powinno być komputerem stacjonarnym, który jest zawsze włączony i dostępny dla klientów równorzędnej pamięci podręcznej.  

-   Równorzędna pamięć podręczna systemu Windows PE musi mieć wystarczający rozmiar pamięci podręcznej klienta do przechowywania obrazów.  

##  <a name="BKMK_PeerCacheRequirements"></a> Wymagania dla klientów korzystających ze źródła równorzędnej pamięci podręcznej systemu Windows PE  
 Aby klienci mogli używać źródła równorzędnej pamięci podręcznej systemu Windows PE, muszą spełniać następujące wymagania:  

-   Klient programu Configuration Manager musi mieć możliwość komunikują się za pośrednictwem następujących portów w sieci:  

    -   Port początkowej emisji w sieci w celu znalezienia źródła równorzędnej pamięci podręcznej. Domyślnie jest to port 8004.  

    -   Port dla zawartości pobierania ze źródła pamięci podręcznej elementu równorzędnego (HTTP i HTTPS). Domyślnie jest to port 8003.  

        > [!TIP]  
        >  Klienci będą używać protokołu HTTPS do pobierania zawartości, jeśli jest on dostępny. Jednakże dla protokołów HTTP i HTTPS jest używany ten sam numer portu.  

-   [Skonfiguruj pamięć podręczną klienta dla klientów programu Configuration Manager](../../core/clients/manage/manage-clients.md#BKMK_ClientCache) na klientach, aby upewnić się, że mają wystarczającą ilość miejsca na przechowywanie wdrażanych obrazów. Równorzędna pamięć podręczna systemu Windows PE nie ma wpływu na konfigurację ani zachowanie pamięci podręcznej klienta.  

-   Opcje wdrażania na potrzeby wdrożenia sekwencji zadań muszą zostać skonfigurowane tak, aby zawartość była pobierana lokalnie, gdy będzie wymagana przez sekwencję zadań.  

##  <a name="BKMK_PeerCacheConfigure"></a> Konfigurowanie równorzędnej pamięci podręcznej systemu Windows PE  
 Możesz użyć poniższych metod w celu aprowizowania zawartości równorzędnej pamięci podręcznej na kliencie, aby służył jako źródło równorzędnej pamięci podręcznej:  

-   Klient równorzędnej pamięci podręcznej, który nie może znaleźć źródła równorzędnej pamięci podręcznej, pobiera zawartość z punktu dystrybucji.  Jeśli klient otrzymał ustawienia klienta włączające równorzędną pamięć podręczną, a sekwencja zadań jest skonfigurowana pod kątem zachowania zawartości w pamięci podręcznej, klient jest źródłem równorzędnej pamięci podręcznej.  

-   Klient pamięci podręcznej elementu równorzędnego umożliwia pobranie zawartości z innego elementu równorzędnego pamięci podręcznej klienta (peer źródła pamięci podręcznej).  Ponieważ klient jest skonfigurowany na potrzeby równorzędnej pamięci podręcznej, gdy działa na nim sekwencja zadań skonfigurowana pod kątem zachowania zawartości w pamięci podręcznej, klient jest źródłem równorzędnej pamięci podręcznej.  

-   Klient uruchamia sekwencję zadań uwzględniającą dodatkowy opcjonalny krok, [Pobierz zawartość pakietu](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent), używany do wstępnego przygotowania odpowiedniej zawartości objętej sekwencją zadań równorzędnej pamięci podręcznej systemu Windows PE. Kiedy należy używać tej metody:  

    -   Zainstalowanie wdrażanego obrazu na kliencie nie jest wymagane.  

    -   Oprócz opcji **Pobierz zawartość pakietu** w sekwencji zadań musi także zostać użyta opcja **Pamięć podręczna klienta programu Configuration Manager** . Ta opcja umożliwia przechowywanie zawartości w pamięci podręcznej klientów, dzięki czemu klient może działać jako źródło równorzędnej pamięci podręcznej dla innych klientów równorzędnej pamięci podręcznej.  

 Poniższe procedury ułatwiają konfigurowanie równorzędnej pamięci podręcznej systemu Windows PE na klientach i umożliwiają konfigurowanie sekwencji zadań obsługujących równorzędną pamięć podręczną.  

### <a name="to-configure-the-windows-pe-peer-cache-source-computers"></a>Aby skonfigurować komputery źródła równorzędnej pamięci podręcznej systemu Windows PE  

1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **ustawień klienta**, a następnie utworzyć nowy **niestandardowych ustawień urządzenia klienckiego** lub zmodyfikować istniejący obiekt ustawień. Równorzędną pamięć podręczną możesz też skonfigurować w ramach obiektu **domyślnych ustawień klienta** .  

    > [!TIP]  
    >  Obiekty ustawień niestandardowych umożliwiają wybieranie klientów otrzymujących konfigurację równorzędnej pamięci podręcznej. Dzięki nim można na przykład uniknąć konfigurowania równorzędnej pamięci podręcznej na komputerach przenośnych użytkowników, którzy są często w ruchu. System, który jest bardzo często przenoszony, nie jest dobrym źródłem zawartości udostępnianej innym klientom równorzędnej pamięci podręcznej.  
    >   
    >  Pamiętaj również, że konfiguracja równorzędnej pamięci podręcznej w ramach **domyślnych ustawień klienta**ma zastosowanie do wszystkich klientów w środowisku.  

2.  W obszarze **Równorzędna pamięć podręczna systemu Windows PE**dla opcji **Włącz klienta programu Configuration Manager w pełnym systemie operacyjnym na potrzeby udostępniania zawartości** ustaw wartość **Tak**.  

    -   Domyślnie włączony jest tylko protokół HTTP. Aby umożliwić klientom pobieranie zawartości przy użyciu protokołu HTTPS, ustaw opcję **Włącz protokół HTTPS na potrzeby komunikacji równorzędnej między klientami** na wartość **Tak**.  

    -   Domyślny port emisji to 8004, a port pobierania zawartości to 8003. Możesz zmienić ustawienie obu tych portów.  

3.  Zapisz i wdróż ustawienia klienta na klientach wybranych jako źródło równorzędnej pamięci podręcznej.  

 Po skonfigurowaniu urządzenia przy użyciu tego obiektu ustawień urządzenie jest gotowe do działania jako źródło równorzędnej pamięci podręcznej. Ustawienia te powinny być wdrażane na potencjalnych klientach równorzędnej pamięci podręcznej w celu skonfigurowania wymaganych pól i protokołów.  

###  <a name="BKMK_PeerCacheConfigureTS"></a> Konfigurowanie sekwencji zadań równorzędnej pamięci podręcznej systemu Windows PE  
 Podczas konfigurowania sekwencji zadań użyj poniższych zmiennych sekwencji zadań jako zmiennych kolekcji, w której wdrażana jest sekwencja:  

-   **SMSTSPeerDownload**  

     Wartość:  WARTOŚĆ TRUE  

     Umożliwia klientowi używanie równorzędnej pamięci podręcznej systemu Windows PE.  

-   **SMSTSPeerRequestPort**  

     Wartość: < numer portu\>  

     Nie należy używać domyślnego portu skonfigurowanym w ustawieniach klienta (8004), należy skonfigurować tę zmienną z niestandardową wartość portu sieci na potrzeby początkowej emisji.  

-   **SMSTSPreserveContent**  

     Wartość: WARTOŚĆ TRUE  

     Flagi to zawartość w sekwencji zadań, które będą przechowywane w pamięci podręcznej klienta programu Configuration Manager po wdrożeniu. To jest inny niż przy użyciu SMSTSPersisContent, który tylko zachowuje zawartość w czasie trwania sekwencji zadań i korzysta z pamięci podręcznej sekwencji zadań, nie Menedżera konfiguracji pamięci podręcznej klienta.  

 Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](../understand/task-sequence-built-in-variables.md).  

###  <a name="BKMK_PeerCacheValidate"></a> Sprawdzanie, czy równorzędna pamięć podręczna systemu Windows PE została pomyślnie użyta  
 Po wdrożeniu i zainstalowaniu sekwencji zadań przy użyciu równorzędnej pamięci podręcznej systemu Windows PE możesz sprawdzić, czy została ona pomyślnie użyta w procesie, przeglądając dziennik **smsts.log** na kliencie, na którym uruchomiono sekwencję zadań.  

 W dzienniku, zlokalizować wpis podobny do następującego gdzie <*Nazwa_serwera_źródłowego*> identyfikuje komputer, z którym klient uzyskuje zawartość. Ten komputer powinien być źródłem równorzędnej pamięci podrzędnej, a nie serwerem punktu dystrybucji. Pozostałe szczegóły różnią się zależnie od lokalnego środowiska i konfiguracji.  

-   *<! [Dziennika [pobrany plik z http:// < Nazwa_serwera_źródłowego\>: 8003/SCCM_BranchCache$/SS10000C/sccm?/install.wim do C:\\_SMSTaskSequence\Packages\SS10000C\install.wim] dziennika]! >< czas = "14:24:33.329 + 420" Data = "06-26-2015" składnika = "ApplyOperatingSystem" kontekst = "" typ = "1" wątku = "1256" file="downloadcontent.cpp:1626" >*  

