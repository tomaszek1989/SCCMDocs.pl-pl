---
title: "Skonfigurować porty komunikacyjne klienta | Dokumentacja firmy Microsoft"
description: Ustaw porty komunikacyjne klienta w programie System Center Configuration Manager.
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 406bbdbf-ab4a-4121-a68b-154f96ea14ec
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstack
ms.author: robstackmsft
manager: angrobe
ms.openlocfilehash: 63e033fdb436930ac5f37e7408ca9292bc444560
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-configure-client-communication-ports-in-system-center-configuration-manager"></a>Jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można zmienić numerów portów żądań, używanego przez klientów programu System Center Configuration Manager do komunikowania się z systemami lokacji wykorzystującymi do komunikacji HTTP i HTTPS. Chociaż HTTP lub HTTPS jest bardziej prawdopodobne, że już być skonfigurowana dla zapór, powiadomienie klienta, który używa protokołu HTTP lub HTTPS wymaga więcej użycie procesora CPU i pamięci na komputerze punktu zarządzania niż w przypadku użycia niestandardowy numer portu. Można również określić numer portu lokacji do użycia, jeśli wznawiania klientów przy użyciu tradycyjnych pakietów wznawiania.  

 Podczas określania portów żądań HTTP i HTTPS, można określić zarówno domyślny numer portu, jak i alternatywny numer portu. Klienci automatycznie próbują użyć portu alternatywnego niepowodzenia komunikacji za pomocą portu domyślnego. Można określić ustawienia dla komunikacji HTTP i HTTPS.  

 Domyślne wartości portów żądań klientów to **80** dla ruchu HTTP i **443** dla ruchu HTTPS. Należy je zmienić tylko wtedy, gdy nie chcesz używać tych wartości domyślnych. Typowy scenariusz użycia portów niestandardowych jest podczas używania niestandardowej witryny sieci Web w usługach IIS, a nie domyślnej witryny sieci Web. Jeśli zmienisz to domyślne numery portów dla domyślnej witryny sieci Web w usługach IIS i inne aplikacje także korzystają domyślnej witryny sieci Web, są one mogą nie działać prawidłowo.  

> [!IMPORTANT]  
>  Nie należy zmieniać numerów portów w programie Configuration Manager bez zrozumienia konsekwencji tego działania. Przykłady:  
>   
>  -   Jeśli zmienisz numery portów dla usług żądań klientów, konfiguracja lokacji i istniejący klienci nie są tak skonfigurować, aby korzystać z nowych numerów portów, Ci klienci staną się Niezarządzani.  
> -   Przed skonfigurowaniem numer portu inny niż domyślny, upewnij się, że zapory i wszystkie pośredniczące urządzenia sieciowe mogą obsłużyć tę konfigurację i skonfigurować je ponownie w razie potrzeby. Jeśli będzie zarządzać klientami w Internecie i zmień domyślny numer portu HTTPS 443, routery i zapory w Internecie mogą zablokować tę komunikację.  

 Aby upewnić się, że klienci nie staną się Niezarządzani po zmianie numerów portów żądań, klientów musi być skonfigurowana do używania nowych numerów portów żądań. Po zmianie portów żądań w lokacji głównej wszystkie podłączone Lokacje dodatkowe automatycznie odziedziczą tę samą konfigurację portów. Procedura w tym temacie służą do konfigurowania portów żądań w lokacji głównej.  

> [!NOTE]  
>  Aby uzyskać informacje dotyczące konfigurowania portów żądań klientów na komputerach z systemem Linux i UNIX, zobacz [Konfigurowanie portów żądań klienta dla systemów Linux i UNIX](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md#BKMK_ConfigLnUClientCommuincations).  

 Po opublikowaniu lokacji programu Configuration Manager w usługach domenowych w usłudze Active Directory, nowych i istniejących klientów, którzy mogą uzyskiwać dostęp do tych informacji zostaną skonfigurowane automatycznie ustawienia portu lokacji i jest konieczne wykonywanie dodatkowych działań. Do klientów, którzy nie mogą uzyskać dostępu do tych informacji opublikowanych w usługach Active Directory Domain Services, zalicza się klientów grup roboczych, klientów z innego lasu usługi Active Directory, klientów skonfigurowanych do pracy tylko w Internecie i klientów aktualnie połączonych z Internetem. W przypadku zmiany domyślnych numerów portów po zainstalowaniu tych klientów, należy zainstalować ich ponownie i zainstalować ewentualnych nowych klientów przy użyciu jednej z następujących metod:  

-   Zainstaluj klientów ponownie, używając Kreatora instalacji wypychanej klienta. Wypychana instalacja klienta automatycznie konfiguruje klientów przy użyciu bieżącej konfiguracji portów lokacji. Aby uzyskać więcej informacji na temat korzystania z Kreatora instalacji wypychanej klienta, zobacz [jak instalować klientów programu Configuration Manager za pomocą wypychania klienta](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

-   Zainstaluj klientów ponownie, używając CCMSetup.exe i właściwości instalacji pliku client.msi CCMHTTPPORT i CCMHTTPSPORT. Aby uzyskać więcej informacji na temat tych właściwości, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

-   Zainstaluj klientów ponownie, używając metody, która wyszukuje właściwości instalacji klientów programu Configuration Manager w usługach Active Directory Domain Services. Aby uzyskać więcej informacji, zobacz [Informacje o właściwościach instalacji klienta publikowanych w Usługach domenowych Active Directory w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties-published-to-active-directory-domain-services.md).  

 Aby ponownie skonfigurować numery portów dla istniejących klientów, można także użyć skryptu PORTSWITCH. VBS, który znajduje się na nośniku instalacyjnym w folderze SMSSETUP\Tools\PortConfiguration.  

> [!IMPORTANT]  
>  Dla istniejących i nowych klientów, które są obecnie w Internecie należy skonfigurować numery portów innych niż domyślne za pomocą właściwości pliku client.msi CCMSetup.exe CCMHTTPPORT i CCMHTTPSPORT.  

 Po zmianie portów żądań w witrynie, nowych klientów, które są instalowane przy użyciu metody instalacji wypychanej klienta w całej lokacji zostaną automatycznie skonfigurowane bieżące numery portów dla tej lokacji.  

#### <a name="to-configure-the-client-communication-port-numbers-for-a-site"></a>Aby skonfigurować numery portów komunikacji klientów dla lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**, kliknij przycisk **witryny**i wybierz lokację główną do skonfigurowania.  

3.  Na **Home** , kliknij pozycję **właściwości**, a następnie kliknij przycisk **porty** kartę.  

4.  Wybierz dowolne elementy i kliknij ikonę właściwości, aby wyświetlić **Szczegóły portu** okno dialogowe.  

5.  W **Szczegóły portu** okno dialogowe, określ numer portu i opis elementu, a następnie kliknij przycisk **OK**.  

6.  Wybierz **Użyj niestandardowej witryny sieci web** Jeśli korzystasz z niestandardowej witryny sieci Web nazwę **SMSWeb** dla systemów lokacji z usługami IIS.  

7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe właściwości tej lokacji.  

 Powtórz te czynności dla wszystkich lokacji podstawowych w hierarchii.
