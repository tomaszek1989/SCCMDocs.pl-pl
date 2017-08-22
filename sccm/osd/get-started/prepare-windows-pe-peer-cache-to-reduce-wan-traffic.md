---
title: "Przygotowywanie równorzędnej pamięci podręcznej systemu Windows PE celu zmniejszenie ruchu w sieci WAN | Dokumentacja firmy Microsoft"
description: "Równorzędna pamięć podręczna systemu Windows PE działa w środowisku Windows PE pobierać zawartość z lokalnego elementu równorzędnego i zminimalizować ruch w sieci WAN, gdy jest żaden lokalny punkt dystrybucji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 6c64f276-b88c-4b1e-8073-331876a03038
caps.latest.revision: "11"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 814c6133a30b1116d05aaeafddb0dfb7fe2a390e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="prepare-windows-pe-peer-cache-to-reduce-wan-traffic-in-system-center-configuration-manager"></a>Przygotowywanie równorzędnej pamięci podręcznej systemu Windows PE w celu zredukowania ruchu w sieci WAN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas wdrażania nowego systemu operacyjnego w programie System Center Configuration Manager, komputery z systemem sekwencji zadań można użyć równorzędnej pamięci podręcznej systemu Windows PE pobierać zawartość z lokalnego elementu równorzędnego (źródła równorzędnej pamięci podręcznej) zamiast z punktu dystrybucji. Minimalizuje to ruch w sieci rozległej w scenariuszach oddziału firmy bez lokalnego punktu dystrybucji.  

 Równorzędna pamięć podręczna systemu Windows PE przypomina [usługi Windows BranchCache](http://technet.microsoft.com/library/mt617255\(TechNet.10\).aspx#bkmk_branchcache), ale działa w środowisku preinstalacji systemu Windows (Windows PE). W przypadku uruchomienia sekwencji zadań w kontekście systemu operacyjnego, na przykład z poziomu programu Software Center na kliencie, równorzędna pamięć podręczna systemu Windows PE nie jest używana. Poniższe terminy są używane do opisywania klientów korzystających z równorzędnej pamięci podręcznej systemu Windows PE:  

-   **Klient równorzędnej pamięci podręcznej** to komputer skonfigurowany do używania równorzędnej pamięci podręcznej systemu Windows PE.  

-   **Źródło równorzędnej pamięci podręcznej** to klient skonfigurowany na potrzeby zapewniania równorzędnej pamięci podręcznej, który udostępnia zawartość innym klientom równorzędnej pamięci podręcznej żądającym tej zawartości.  

Poniższe sekcje umożliwia zarządzanie równorzędnej pamięci podręcznej.

##  <a name="BKMK_PeerCacheObjects"></a> Obiekty przechowywane w źródle równorzędnej pamięci podręcznej  
 Sekwencja zadań skonfigurowana do korzystania z równorzędnej pamięci podręcznej systemu Windows PE może uzyskać następujące obiekty zawartości podczas pracy w systemie Windows PE:  

-   Obraz systemu operacyjnego  

-   Pakiety sterowników  

-   Pakiety i programy (gdy klient kontynuuje działanie sekwencji zadań w pełnym systemie operacyjnym, klient pobiera zawartość ze źródła równorzędnej pamięci podręcznej Jeśli sekwencja zadań była wcześniej skonfigurowana równorzędnej pamięci podręcznej podczas uruchamiania w środowisku Windows PE.)  

-   Dodatkowe obrazy rozruchowe  

 Następujące obiekty zawartości nigdy nie są przesyłane przy użyciu równorzędnej pamięci podręcznej. Zamiast tego są przesyłane z punktu dystrybucji lub za pomocą usługi Windows BranchCache, jeśli w środowisku skonfigurowano tę usługę:  

-   Aplikacje  

-   Aktualizacje oprogramowania  

##  <a name="BKMK_PeerCacheWork"></a> Jak działa równorzędna pamięć podręczna systemu Windows PE?  
 Rozważmy scenariusz biura oddziału bez punktu dystrybucji, ale z włączoną obsługą równorzędnej pamięci podręcznej systemu Windows PE na kilku klientach. Sekwencja zadań skonfigurowana do korzystania z równorzędnej pamięci podręcznej jest wdrażana na kilku klientach skonfigurowanych jako część źródła równorzędnej pamięci podręcznej. Pierwszy klient, na którym uruchomiono sekwencję zadań, emituje żądanie w poszukiwaniu elementu równorzędnego z zawartością. Nie znajduje takiego elementu, więc pobiera zawartość z punktu dystrybucji w sieci WAN. Klient instaluje nowy obraz, a następnie przechowuje zawartość w pamięci podręcznej klienta programu Configuration Manager, dzięki czemu może działać jako źródło równorzędnej pamięci podręcznej dla innych klientów. Po uruchomieniu przez następnego klienta sekwencji zadań klient ten emituje żądanie w podsieci dotyczące źródła równorzędnej pamięci podręcznej. Odpowiada pierwszy klient i udostępnia zawartość znajdującą się w jego pamięci podrzędnej.  

##  <a name="BKMK_PeerCacheDetermine"></a> Określanie, którzy klienci będą częścią źródła równorzędnej pamięci podręcznej systemu Windows PE  
 Aby ułatwić określenie, które komputery wybrać jako źródło równorzędnej pamięci podręcznej systemu Windows PE, należy wziąć pod uwagę kilka kwestii:  

-   Źródło równorzędnej pamięci podręcznej systemu Windows PE powinno być komputerem stacjonarnym, który jest zawsze włączony i dostępny dla klientów równorzędnej pamięci podręcznej.  

-   Równorzędna pamięć podręczna systemu Windows PE musi mieć wystarczający rozmiar pamięci podręcznej klienta do przechowywania obrazów.  

##  <a name="BKMK_PeerCacheRequirements"></a> Wymagania dla klientów korzystających ze źródła równorzędnej pamięci podręcznej systemu Windows PE  
 Aby klienci mogli używać źródła równorzędnej pamięci podręcznej systemu Windows PE, muszą spełniać następujące wymagania:  

-   Klienta programu Configuration Manager musi mieć możliwości komunikacji przy użyciu poniższych portów w sieci:  

    -   Port początkowej emisji w sieci w celu znalezienia źródła równorzędnej pamięci podręcznej. Domyślnie jest to port 8004.  

    -   Port pobierania zawartości ze źródła równorzędnej pamięci podręcznej (protokół HTTP i HTTPS). Domyślnie jest to port 8003.  

        > [!TIP]  
        >  Klienci będą używać protokołu HTTPS do pobierania zawartości, jeśli jest on dostępny. Jednakże dla protokołów HTTP i HTTPS jest używany ten sam numer portu.  

-   [Skonfiguruj pamięć podręczną klienta dla klientów programu Configuration Manager](../../core/clients/manage/manage-clients.md#BKMK_ClientCache) na klientach, aby upewnić się, że mają wystarczającą ilość miejsca na przechowywanie wdrażanych obrazów. Równorzędna pamięć podręczna systemu Windows PE nie ma wpływu na konfigurację ani zachowanie pamięci podręcznej klienta.  

-   Opcje wdrażania na potrzeby wdrożenia sekwencji zadań muszą zostać skonfigurowane tak, aby zawartość była pobierana lokalnie, gdy będzie wymagana przez sekwencję zadań.  

##  <a name="BKMK_PeerCacheConfigure"></a> Konfigurowanie równorzędnej pamięci podręcznej systemu Windows PE  
 Możesz użyć poniższych metod w celu aprowizowania zawartości równorzędnej pamięci podręcznej na kliencie, aby służył jako źródło równorzędnej pamięci podręcznej:  

-   Klient równorzędnej pamięci podręcznej, który nie może znaleźć źródła równorzędnej pamięci podręcznej, pobiera zawartość z punktu dystrybucji.  Jeśli klient otrzymał ustawienia klienta włączające równorzędną pamięć podręczną, a sekwencja zadań jest skonfigurowana pod kątem zachowania zawartości w pamięci podręcznej, klient jest źródłem równorzędnej pamięci podręcznej.  

-   Klient równorzędnej pamięci podręcznej może pobierać zawartość z innego klienta pamięci podręcznej elementu równorzędnego (źródła równorzędnej pamięci podręcznej).  Ponieważ klient jest skonfigurowany na potrzeby równorzędnej pamięci podręcznej, gdy działa na nim sekwencja zadań skonfigurowana pod kątem zachowania zawartości w pamięci podręcznej, klient jest źródłem równorzędnej pamięci podręcznej.  

-   Klient uruchamia sekwencję zadań uwzględniającą dodatkowy opcjonalny krok, [Pobierz zawartość pakietu](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent), używany do wstępnego przygotowania odpowiedniej zawartości objętej sekwencją zadań równorzędnej pamięci podręcznej systemu Windows PE. Kiedy należy używać tej metody:  

    -   Zainstalowanie wdrażanego obrazu na kliencie nie jest wymagane.  

    -   Oprócz opcji **Pobierz zawartość pakietu** w sekwencji zadań musi także zostać użyta opcja **Pamięć podręczna klienta programu Configuration Manager** . Ta opcja umożliwia przechowywanie zawartości w pamięci podręcznej klientów, dzięki czemu klient może działać jako źródło równorzędnej pamięci podręcznej dla innych klientów równorzędnej pamięci podręcznej.  

 Poniższe procedury ułatwiają konfigurowanie równorzędnej pamięci podręcznej systemu Windows PE na klientach i umożliwiają konfigurowanie sekwencji zadań obsługujących równorzędną pamięć podręczną.  

### <a name="to-configure-the-windows-pe-peer-cache-source-computers"></a>Aby skonfigurować komputery źródła równorzędnej pamięci podręcznej systemu Windows PE  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **ustawień klienta**, a następnie utwórz nową **niestandardowych ustawień urządzenia klienckiego** lub Edytuj istniejący obiekt ustawień. Równorzędną pamięć podręczną możesz też skonfigurować w ramach obiektu **domyślnych ustawień klienta** .  

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

     Jeśli nie używasz domyślnego portu skonfigurowanego w ustawieniach klienta (8004), tę zmienną musisz skonfigurować przy użyciu niestandardowej wartości portu sieci używanego podczas początkowej emisji.  

-   **SMSTSPreserveContent**  

     Wartość: WARTOŚĆ TRUE  

     Oznacza flagą zawartość w sekwencji zadań, która ma zostać zachowana w pamięci podręcznej klienta programu Configuration Manager po wdrożeniu. Sytuacja ta różni się od zmiennej smstspersiscontent, tylko zachowuje zawartość w czasie trwania sekwencji zadań, która używa pamięci podręcznej sekwencji zadań, nie programu Configuration Manager pamięci podręcznej klienta.  

 Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](../understand/task-sequence-built-in-variables.md).  

###  <a name="BKMK_PeerCacheValidate"></a> Sprawdzanie, czy równorzędna pamięć podręczna systemu Windows PE została pomyślnie użyta  
 Po wdrożeniu i zainstalowaniu sekwencji zadań przy użyciu równorzędnej pamięci podręcznej systemu Windows PE możesz sprawdzić, czy została ona pomyślnie użyta w procesie, przeglądając dziennik **smsts.log** na kliencie, na którym uruchomiono sekwencję zadań.  

 W dzienniku Znajdź wpis przypominający poniższy gdzie <*Nazwa_serwera_źródła*> identyfikuje komputer, z którego klient uzyskał zawartość. Ten komputer powinien być źródłem równorzędnej pamięci podrzędnej, a nie serwerem punktu dystrybucji. Pozostałe szczegóły różnią się zależnie od lokalnego środowiska i konfiguracji.  

-   *<! [Dziennika [Downloaded file from http:// < Nazwa_serwera_źródła\>: 8003/SCCM_BranchCache$/SS10000C/sccm?/install.wim do folderu C:\\_SMSTaskSequence\Packages\SS10000C\install.wim] dziennika]! >< czas = "14:24:33.329 + 420" date = "06-26-2015" component = "ApplyOperatingSystem" context = "" typ = "1" thread = "1256" file="downloadcontent.cpp:1626" >*  
