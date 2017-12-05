---
title: "Witryny sieci Web dla systemów lokacji"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat domyślnych i niestandardowych witryn sieci Web serwerów systemu lokacji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 681f0893-e83b-476e-9ec0-a5dc7c9deeb6
caps.latest.revision: "15"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 7d91bc91ec1992ecf06244adf48b76332fc25a1b
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="websites-for-site-system-servers-in-system-center-configuration-manager"></a>Witryny sieci Web serwerów systemu lokacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Niektóre role systemu lokacji programu Configuration Manager wymaga użycia Microsoft Internet Information Services (IIS) i użyj domyślnej witryny usług IIS do hostowania usług systemu lokacji. Po uruchomieniu innych aplikacji sieci web na ten sam serwer i ustawienia nie są zgodne z programem Configuration Manager, należy rozważyć użycie niestandardowej witryny sieci Web dla programu Configuration Manager.  

> [!TIP]  
>  Ze względów bezpieczeństwa jest dedykowanego serwera do systemów lokacji programu Configuration Manager, które wymagają usług IIS. Uruchamianie innych aplikacji programu Configuration Manager systemu lokacji, zwiększa podatność na tym komputerze.  




##  <a name="BKMK_What2Know"></a>Co należy wiedzieć przed wybraniem opcji użycia niestandardowych witryn sieci Web  
 Domyślnie role systemu lokacji używają **domyślnej witryny sieci Web** w usługach IIS. To jest skonfigurowane automatycznie podczas instalowania roli systemu lokacji. Jednak w lokacjach głównych można użyć niestandardowych witryn sieci Web. W przypadku korzystania z niestandardowych witryn sieci Web:  

-   Niestandardowych witryn sieci Web są włączane dla całej lokacji, a nie dla poszczególnych serwerów lub systemu lokacji ról.  

-   W lokacjach głównych każdy komputer, który będzie hostować odpowiednią rolę systemu lokacji musi zostać skonfigurowany z niestandardowej witryny sieci Web o nazwie **SMSWEB**. Dopiero po utworzeniu tej witryny sieci Web i skonfiguruj role systemu lokacji na tym komputerze, aby użyć niestandardowej witryny sieci Web, klienci mogą nie mieć możliwości komunikacji z rolami systemu lokacji na tym komputerze.  

-   Ponieważ Lokacje dodatkowe są automatycznie konfigurowane do używania niestandardowej witryny sieci Web, po skonfigurowaniu ich nadrzędnej lokacji głównej w tym celu należy także utworzyć niestandardowych witryn sieci Web w usługach IIS na każdym serwerze systemu lokacji dodatkowej, który wymaga usług IIS.  


  **Wymagania wstępne dotyczące korzystania z niestandardowych witryn sieci Web:**  

 Przed włączeniem opcji użycia niestandardowych witryn sieci Web w lokacji należy:  

-   Utworzyć niestandardową witrynę sieci Web o nazwie **SMSWEB** w usługach IIS na wszystkich serwerach systemu lokacji, które wymagają usług IIS. Wykonaj tę czynność w lokacji głównej i we wszystkich podrzędnych lokacjach dodatkowych.  

-   Skonfiguruj niestandardową witrynę sieci Web odpowiedzieć na tego samego portu, który skonfigurowany do komunikacji z klientem programu Configuration Manager (port żądania klienta).  

-   Dla każdej niestandardowej lub domyślnej witryny internetowej używającej niestandardowego folderu, Umieść kopię domyślny dokument typ używanej w folderze głównym hostującym witrynę internetową. Na przykład na komputerze z systemem Windows Server 2008 R2, który ma domyślne konfiguracje **iisstart.htm** jest jednym z kilku domyślnego typów dokumentów, które są dostępne. Można znaleźć tego pliku w katalogu głównym domyślnej witryny sieci Web, a następnie umieść kopię tego pliku (lub kopię używanego typu dokumentu domyślnego) w folderze głównym hostującym niestandardową witrynę internetową SMSWEB. Aby uzyskać więcej informacji na temat typów dokumentu domyślnego, zobacz [dokument domyślny &lt;defaultDocument\> dla usług IIS](http://www.iis.net/configreference/system.webserver/defaultdocument).  

**O wymaganiach dotyczących usług IIS:**
**następujące role systemu lokacji wymagają usług IIS i witryny sieci Web do hostowania usług systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt dystrybucji  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania  

-   Punkt aktualizacji oprogramowania  

-   Punkt migracji stanu  

Dodatkowe kwestie do rozważenia:  

-   Gdy lokacja główna ma niestandardowych witryn sieci Web, które są włączone, klienci przypisani do tej lokacji są kierowane do komunikowania się z niestandardowych witryn sieci Web zamiast domyślnymi witrynami sieci Web na odpowiednich serwerach systemu lokacji  

-   Jeśli używasz niestandardowych witryn sieci Web dla jednej z lokacji głównej, należy wziąć pod uwagę niestandardowych witryn sieci Web dla wszystkich lokacji głównych w hierarchii, aby upewnić się, że klienci mogą pomyślny roaming między lokacjami hierarchii. (Roaming ma miejsce, jeśli komputer klienta przemieszcza się do nowego segmentu sieci, który jest zarządzany przez inną lokację. Roaming może mieć wpływ na zasoby, które klient może uzyskiwać dostęp lokalnie zamiast przez łącze WAN).  

-   Role systemu lokacji, które używają programu IIS, ale nie akceptują połączeń klientów, takie jak punkt usług raportowania, również korzystają z witryny sieci Web SMSWEB zamiast domyślnej witryny sieci Web.  

-   Niestandardowych witryn sieci Web wymagają przypisania numerów portów innych niż te, które korzysta z komputera domyślnej witryny sieci Web. Domyślna witryna sieci Web oraz niestandardowa witryna sieci Web nie mogą działać jednocześnie, jeśli obie próbują używać tych samych portów TCP/IP.  

-   Porty TCP/IP konfigurowane w usługach IIS dla niestandardowej witryny sieci Web muszą być zgodne z portami żądań klientów dla lokacji.  

## <a name="switch-between-default-and-custom-websites"></a>Przełączanie między domyślnymi i niestandardowymi witrynami sieci Web  
Mimo że można sprawdzić lub usuń zaznaczenie pola dotyczące korzystania z niestandardowych witryn sieci Web w lokacji głównej w dowolnym momencie (pole znajduje się na karcie Ogólne we właściwościach lokacji), należy dokładnie zaplanować przed wprowadzeniem tej zmiany. Po zmianie tej konfiguracji, wszystkich odpowiednich ról systemu lokacji w lokacji głównej i dodatkowej lokacji podrzędnych należy odinstalować i ponownie:  

Następujące role **są ponownie instalowane automatycznie**:  

-   Punkt zarządzania  

-   Punkt dystrybucji  

-   Punkt aktualizacji oprogramowania  

-   Rezerwowy punkt stanu  

-   Punkt migracji stanu  

Następujące role należy **ponownie zainstalować ręcznie**:  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

Dodatkowo:  

-   Jeśli zmienisz z domyślnej witryny sieci Web do używania niestandardowej witryny sieci Web, programu Configuration Manager nie usuwa starych katalogów wirtualnych. Jeśli chcesz usunąć pliki używane w programie Configuration Manager, należy ręcznie usunąć katalogi wirtualne utworzone w ramach domyślnej witryny sieci Web.  

-   Jeśli zmienisz lokacji do używania niestandardowych witryn sieci Web klientów, którzy zostali przypisani do lokacji następnie należy skonfigurować do używania nowych portów żądań klienta dla niestandardowych witryn sieci Web. Zobacz [jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md).  

## <a name="set-up-custom-websites"></a>Konfigurowanie niestandardowych witryn sieci Web  
Ponieważ kroki tworzenia niestandardowej witryny sieci Web są różne w różnych wersjach systemów operacyjnych, zapoznaj się z dokumentacją dotyczącą Twojej wersji systemu operacyjnego, aby uzyskać szczegółowe instrukcje na temat kroków, ale skorzystaj również z poniższych informacji, jeśli mają zastosowanie:  

-   Nazwa witryny sieci Web muszą być: **SMSWEB**.  

-   Podczas konfigurowania protokołu HTTPS, należy określić certyfikat SSL, zanim będzie można zapisać konfiguracji.  

-   Po utworzeniu niestandardowej witryny sieci Web Usuń porty niestandardowej witryny sieci Web, których używasz z innych witryn sieci Web w usługach IIS:  

    1.  Edytuj **powiązania** innych witryn sieci Web, aby usunąć porty odpowiadające przypisanych do **SMSWEB** witryny sieci Web.  

    2.  Uruchom **SMSWEB** witryny sieci Web.  

    3.  Uruchom ponownie usługę **SMS_SITE_COMPONENT_MANAGER** na serwerze lokacji witryny.  
