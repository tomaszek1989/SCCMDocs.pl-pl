---

title: Monitorowanie aktualizacji oprogramowania | Dokumentacja firmy Microsoft
description: "Konsola programu System Center Configuration Manager zapewnia alertów i stany do monitorowania zgodności i aktualizacji."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 11/10/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 9afd7b0f-5c8e-48bc-9a65-1f7d74103688
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: 956ef263a1c178b5ab5926705859f4b2d0ae5bc7
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="monitor-software-updates-in-system-center-configuration-manager"></a>Monitorowanie aktualizacji oprogramowania System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager oferuje wiele sposobów ułatwiają monitorowanie obiektów aktualizacji oprogramowania, procesów i informacje o zgodności. Poniższe sekcje służą do monitorowania aktualizacji oprogramowania.

## <a name="software-updates-dashboard"></a>Pulpit nawigacyjny aktualizacji oprogramowania
Począwszy od programu Configuration Manager w wersji 1610 umożliwia pulpitu nawigacyjnego aktualizacje oprogramowania wyświetlić bieżący stan zgodności urządzeń w Twojej organizacji i szybsze analizowanie danych, aby zobaczyć, które urządzenia są zagrożone. Aby wyświetlić pulpit nawigacyjny, przejdź do **monitorowanie** > **Przegląd** > **zabezpieczeń** > **pulpitu nawigacyjnego aktualizacji oprogramowania**.   

##  <a name="BKMK_SUAlerts"></a> Alerty dotyczące aktualizacji oprogramowania  
 Można skonfigurować alerty dotyczące aktualizacji oprogramowania w celu powiadamiania użytkowników administracyjnych, gdy poziom zgodności wdrożeń aktualizacji oprogramowania będzie niższy od skonfigurowanej wartości procentowej. Można skonfigurować alerty dotyczące wdrożeń aktualizacji oprogramowania w następujących lokalizacjach:  

-   Ustawienie ADR: Można skonfigurować ustawienia alertów w kreatorze reguły wdrażania automatycznego oraz właściwościach dla ADR.  

-   Ustawienie wdrożenia: Można skonfigurować ustawienia alertów w Kreatorze wdrażania aktualizacji oprogramowania oraz właściwościach wdrożenia.  

Po skonfigurowaniu ustawień alertów po wystąpieniu określonego warunku, program Configuration Manager generuje alert. Alerty dotyczące aktualizacji oprogramowania można przeglądać w następujących lokalizacjach:  

1.  Ostatnie alerty można przeglądać w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

2.  Skonfigurowanymi alertami można zarządzać w węźle **Alerty** w obszarze roboczym **Monitorowanie** .  

##  <a name="BKMK_SUSyncStatus"></a> Stan synchronizacji aktualizacji oprogramowania  
 Po zainicjowaniu procesu synchronizacji można monitorować proces synchronizacji z konsoli programu Configuration Manager dla wszystkich punktów aktualizacji oprogramowania w hierarchii. Aby monitorować proces synchronizacji aktualizacji oprogramowania, należy użyć następującej procedury.  

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>Aby monitorować proces synchronizacji aktualizacji oprogramowania  

- W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **Przegląd** > **stan synchronizacji punktu aktualizacji oprogramowania**.  

    Punkty aktualizacji oprogramowania w hierarchii programu Configuration Manager są wyświetlane w okienku wyników. Z poziomu tego widoku możesz monitorować stan synchronizacji wszystkich punktów aktualizacji oprogramowania. Aby wyświetlić bardziej szczegółowe informacje na temat procesu synchronizacji, można przejrzeć plik wsyncmgr.log file, znajdujący się w <*Ścieżkainstalacjiprogramuconfigmgr*> \Logs na każdym serwerze lokacji.  

##  <a name="BKMK_SUDeployStatus"></a> stan wdrożenia aktualizacji oprogramowania,  
 Po wdrożeniu aktualizacji oprogramowania w grupie aktualizacji lub pojedynczej aktualizacji oprogramowania można monitorować stan wdrożenia. Aby monitorować stan wdrożenia grupy aktualizacji oprogramowania lub pojedynczej aktualizacji oprogramowania, należy wykonać następującą procedurę.  

#### <a name="to-monitor-deployment-status"></a>Aby monitorować stan wdrożenia  

1.  W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **Przegląd** > **wdrożeń**.  

2.  Kliknij grupę aktualizacji oprogramowania lub aktualizację oprogramowania, których stan wdrożenia chcesz monitorować.  

3.  Na karcie **Narzędzia główne** w grupie **Wdrożenie** kliknij przycisk **Wyświetl stan**.  

##  <a name="BKMK_SUReports"></a> Raporty dotyczące aktualizacji oprogramowania  
 Komunikaty stanu dotyczące aktualizacji oprogramowania zawierają informacje na temat zgodności aktualizacji oprogramowania oraz stanu szacowania i wymuszenia wdrożeń aktualizacji oprogramowania. Aby wyświetlić owe komunikatu stanu, można uruchomić funkcję raportów dotyczących aktualizacji oprogramowania. Istnieje ponad 30 wstępnie zdefiniowanych raportów dotyczących aktualizacji oprogramowania. Są one podzielone na różne kategorie i można ich używać do raportowania określonych informacji dotyczących aktualizacji oprogramowania i wdrożeń. Oprócz wstępnie skonfigurowanych raportów można również tworzyć niestandardowe raporty dotyczące aktualizacji oprogramowania w zależności od potrzeb danej organizacji. Aby uzyskać więcej informacji, zobacz [operacje i Obsługa raportowania](../../core/servers/manage/operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_MonitorContent"></a> Monitorowanie zawartości  
 Można monitorować zawartość w konsoli programu Configuration Manager, aby sprawdzić stan dla wszystkich typów pakietów w odniesieniu do powiązanych punktów dystrybucji. Może to dotyczyć między innymi stanu sprawdzania poprawności zawartości pakietu, stanu zawartości przypisanej do konkretnej grupy punktów dystrybucji, stanu zawartości przypisanej do punktu dystrybucji oraz stanu funkcji opcjonalnych poszczególnych punktów dystrybucji (sprawdzanie poprawności zawartości, środowiska PXE oraz multiemisji).  

###  <a name="BKMK_ContentStatus"></a> Monitorowanie stanu zawartości  
 Węzeł **Stan zawartości** w obszarze roboczym **Monitorowanie** zawiera informacje na temat pakietów zawartości. Można w nim wyświetlić ogólne informacje dotyczące pakietu, jego stanu dystrybucji oraz szczegółowe informacje o stanie pakietu. Aby wyświetlić stan zawartości, należy wykonać następujące czynności.  

#### <a name="to-monitor-content-status"></a>Aby monitorować stan zawartości  

1.  W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **Przegląd** > **stan dystrybucji** > **stan zawartości**. Są wyświetlane pakiety.  

2.  Wybierz pakiet, dla którego chcesz wyświetlić szczegółowe informacje o stanie.  

3.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie pakietu.  

###  <a name="BKMK_DPGroupStatus"></a> Stan grupy punktów dystrybucji  
 Węzeł **Stan grup punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje dotyczące grup punktów dystrybucji. Można w nim przejrzeć informacje ogólne dotyczące grupy punktów dystrybucji, na przykład stanu grupy punktów dystrybucji i poziom zgodności, a także szczegółowe informacje o stanie grupy punktów dystrybucji. Aby wyświetlić stan grupy punktów dystrybucji, należy wykonać następującą procedurę.  

#### <a name="to-monitor-distribution-point-group-status"></a>Aby monitorować stan grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **Przegląd** > **stan dystrybucji** > **stan grupy punktów dystrybucji**. Zostaną wyświetlone grupy punktów dystrybucji.  

2.  Wybierz grupę punktów dystrybucji, dla której chcesz wyświetlić szczegółowe informacje o stanie.  

3.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie grupy punktów dystrybucji.  

###  <a name="BKMK_DPConfigStatus"></a> Stan konfiguracji punktów dystrybucji  
 Węzeł **Stan konfiguracji punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje o punkcie dystrybucji. Można w nim sprawdzić atrybuty włączone w punkcie dystrybucji, jak na przykład środowisko PXE, multiemisja lub sprawdzanie poprawności zawartości. Można również wyświetlić szczegółowe informacje o stanie punktu dystrybucji. Aby wyświetlić stan konfiguracji punktów dystrybucji, należy wykonać następującą procedurę.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>Aby monitorować stan konfiguracji punktów dystrybucji  

1.  W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **Przegląd** > **stan dystrybucji** > **stan konfiguracji punktów dystrybucji**. Zostaną wyświetlone punkty dystrybucji.  

2.  Wybierz punkt dystrybucji, dla którego mają być wyświetlone informacje o stanie punktu dystrybucji.  

3.  W okienku wyników kliknij kartę **Szczegóły** . Zostaną wyświetlone informacje o stanie punktu dystrybucji.  
