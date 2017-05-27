---
title: Witryn sieci Web w systemach lokacji | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat domyślnych i niestandardowych witryn sieci Web na serwerach systemu lokacji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 681f0893-e83b-476e-9ec0-a5dc7c9deeb6
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26bbec1e8d6c53ce297689ba4390b9347229eb15
ms.openlocfilehash: 886ff3b8e867fc340c79648a57feae81653b0ccd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="websites-for-site-system-servers-in-system-center-configuration-manager"></a>Witryny sieci Web serwerów systemu lokacji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Niektóre role systemu lokacji programu Configuration Manager należy użyć programu Microsoft Internet Information Services (IIS) i użyj domyślnej witryny internetowej usług IIS do hosta usług systemu lokacji. Po uruchomieniu innych aplikacji sieci web na tego samego serwera i ustawienia nie są zgodne z programem Configuration Manager, należy rozważyć użycie niestandardowej witryny sieci Web dla programu Configuration Manager.  

> [!TIP]  
>  Ze względów bezpieczeństwa jest należy wyznaczyć serwer dla systemów lokacji programu Configuration Manager, które wymagają usług IIS. Uruchamianie innych aplikacji na Menedżera konfiguracji systemu lokacji, zwiększa obszar ataków tego komputera.  




##  <a name="BKMK_What2Know"></a>Co należy wiedzieć przed wybraniem do używania niestandardowych witryn sieci Web  
 Domyślnie role systemu lokacji używają **domyślnej witryny sieci Web** w usługach IIS. To jest skonfigurowany automatycznie podczas instalowania roli systemu lokacji. Jednak w lokacjach głównych można użyć niestandardowych witryn sieci Web. W przypadku korzystania z niestandardowych witryn sieci Web:  

-   Niestandardowych witryn sieci Web są włączone dla całej lokacji, a nie dla poszczególnych serwerów lub systemu lokacji ról.  

-   W lokacjach głównych, należy skonfigurować każdy komputer, który będzie obsługiwać odpowiednią rolę systemu lokacji z niestandardowej witryny sieci Web o nazwie **SMSWEB**. Do czasu utworzenia tej witryny sieci Web i skonfigurować role systemu lokacji na tym komputerze do używania niestandardowej witryny sieci Web, klienci nie może być mogły komunikować się z rolami systemu lokacji na tym komputerze.  

-   Ponieważ Lokacje dodatkowe są automatycznie konfigurowane do używania niestandardowej witryny sieci Web, gdy ich nadrzędnej lokacji głównej tego dokonać, należy także utworzyć niestandardowych witryn sieci Web w usługach IIS, na każdym serwerze systemu lokacji dodatkowej, który wymaga usług IIS.  


  **Wymagania wstępne dotyczące korzystania z niestandardowych witryn sieci Web:**  

 Przed włączeniem opcji użycia niestandardowych witryn sieci Web w lokacji należy:  

-   Utworzyć niestandardową witrynę sieci Web o nazwie **SMSWEB** w usługach IIS na wszystkich serwerach systemu lokacji, które wymagają usług IIS. Wykonaj tę czynność w lokacji głównej i we wszystkich podrzędnych lokacjach dodatkowych.  

-   Skonfiguruj niestandardową witrynę sieci Web, odpowiadanie na tym samym porcie, który skonfigurowany do komunikacji z klientem programu Configuration Manager (portu żądań klienta).  

-   Dla każdego niestandardowego lub domyślnej witryny internetowej używającej niestandardowego folderu, Umieść kopię domyślny dokument typu, którego używasz w folderze głównym, który jest hostem witryny sieci Web. Na przykład na komputerze z systemem Windows Server 2008 R2 domyślne konfiguracje **iisstart.htm** jest jednym z kilku domyślnych typów dokumentów, które są dostępne. Można odnaleźć tego pliku w katalogu głównym domyślnej witryny sieci Web, a następnie umieść kopię tego pliku (lub kopię używanego typu dokumentu domyślnego) w folderze głównym hostującym niestandardową witrynę internetową SMSWEB. Szczegółowe informacje na temat typów dokumentu domyślnego, zobacz [dokument domyślny &lt;defaultDocument\> dla usług IIS](http://www.iis.net/configreference/system.webserver/defaultdocument).  

**O wymaganiach dotyczących usług IIS:**
**następujące role systemu lokacji wymagają usług IIS i witryny sieci Web obsługiwała usługi systemu lokacji:**  

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

-   Gdy lokacji głównej ma włączone niestandardowych witryn sieci Web, przekierowany do komunikowania się z niestandardowych witryn sieci Web zamiast domyślnej witryn sieci Web na serwerach systemu lokacji odpowiednich klientów przypisanych do tej witryny  

-   Jeśli używasz niestandardowych witryn sieci Web dla jednej z lokacji głównej, należy wziąć pod uwagę niestandardowych witryn sieci Web dla wszystkich lokacji głównych w hierarchii, aby upewnić się, że klienci mogą pomyślnie przechodzić w hierarchii. (Roaming ma miejsce, jeśli komputer klienta przemieszcza się do nowego segmentu sieci, który jest zarządzany przez inną lokację. Roaming mogą mieć wpływ na zasoby, które klient może uzyskać dostęp lokalnie zamiast przez łącze WAN).  

-   Role systemu lokacji, które używają usług IIS, ale nie akceptują połączeń klientów, takie jak punkt usług raportowania, również użyć witryny sieci Web SMSWEB zamiast domyślnej witryny sieci Web.  

-   Niestandardowych witryn sieci Web wymaga przypisać numery portów, które różnią się od tych, które używa komputera domyślnej witryny sieci Web. Domyślna witryna sieci Web oraz niestandardowa witryna sieci Web nie mogą działać jednocześnie, jeśli obie próbują używać tych samych portów TCP/IP.  

-   Porty TCP/IP ustawione w usługach IIS dla niestandardowej witryny sieci Web muszą być zgodne z portami żądań klientów dla lokacji.  

## <a name="switch-between-default-and-custom-websites"></a>Przełączanie między domyślnych i niestandardowych witryn sieci Web  
Mimo że można sprawdzić lub usuń zaznaczenie pola do używania niestandardowych witryn sieci Web w lokacji głównej w dowolnym momencie (pole jest na karcie Ogólne we właściwościach lokacji), należy dokładnie zaplanować przed wprowadzeniem tej zmiany. Zmiana ta konfiguracja wszystkich odpowiednich ról systemu lokacji w lokacji głównej i dodatkowej lokacji podrzędnych musi odinstalowanie i ponowne zainstalowanie:  

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

-   Po zmianie z domyślnej witryny sieci Web do używania niestandardowej witryny sieci Web programu Configuration Manager nie usuwa starych katalogów wirtualnych. Aby usunąć pliki używane przez program Configuration Manager, należy ręcznie usunąć katalogi wirtualne, które zostały utworzone w ramach domyślnej witryny sieci Web.  

-   Jeśli zmienisz lokacji do używania niestandardowych witryn sieci Web klientów, które są już przypisane do lokacji następnie musi konfigurowane do używania niestandardowych witryn sieci Web nowe porty żądań klientów. Zobacz [jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md).  

## <a name="set-up-custom-websites"></a>Konfigurowanie niestandardowych witryn sieci Web  
Ponieważ kroki tworzenia niestandardowej witryny sieci Web są różne w różnych wersjach systemów operacyjnych, zapoznaj się z dokumentacją dotyczącą Twojej wersji systemu operacyjnego, aby uzyskać szczegółowe instrukcje na temat kroków, ale skorzystaj również z poniższych informacji, jeśli mają zastosowanie:  

-   Nazwa witryny sieci Web muszą być: **SMSWEB**.  

-   Podczas konfigurowania protokołu HTTPS, należy wskazać certyfikat SSL, przed zapisaniem konfiguracji.  

-   Po utworzeniu niestandardowej witryny sieci Web, Usuń porty niestandardowej witryny sieci Web, które można używać z innych witryn sieci Web w usługach IIS:  

    1.  Edytuj **powiązania** innych witryn sieci Web, aby usunąć te same przypisanych do **SMSWEB** witryny sieci Web.  

    2.  Uruchom **SMSWEB** witryny sieci Web.  

    3.  Uruchom ponownie usługę **SMS_SITE_COMPONENT_MANAGER** na serwerze lokacji witryny.  

