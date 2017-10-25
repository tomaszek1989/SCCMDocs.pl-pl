---
title: "Monitorowanie wdrożeń systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Aby ułatwić do monitorowania obiektów wdrożenia systemu operacyjnego, konsoli programu Configuration Manager zawiera alertów, raportów i różnych wskaźniki stanu."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 08085d94-295c-432f-b5e3-9736bce0193b
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 154c0a286e6b9ccedc7545eb010967ac00d35407
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="monitor-operating-system-deployments-in-system-center-configuration-manager"></a>Monitorowanie wdrożeń systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Konsoli programu Configuration Manager oferuje następujące sposoby ułatwiają monitorowanie obiekty wdrożenia systemu operacyjnego.  


##  <a name="BKMK_OSDAlerts"></a> Alerty wdrożeń systemu operacyjnego  
 Możesz skonfigurować alert w ustawieniach wdrażania sekwencji zadań w celu powiadomienia użytkowników administracyjnych, gdy poziom zgodności wdrożenia jest niższy od skonfigurowanej wartości procentowej.  

 Po skonfigurowaniu ustawień alertów po wystąpieniu określonego warunku, program Configuration Manager generuje alert. Możesz przejrzeć alerty dotyczące wdrażania sekwencji zadań w następujących lokalizacjach:  

1.  Najnowsze alerty możesz przejrzeć w węźle **Systemy operacyjne** w obszarze roboczym **Biblioteka oprogramowania** .  

2.  Skonfigurowanymi alertami można zarządzać w węźle **Alerty** w obszarze roboczym **Monitorowanie** .  

##  <a name="BKMK_TSDeployStatus"></a> Stan wdrożenia sekwencji zadań  
 Po wdrożeniu sekwencji zadań możesz monitorować stan wdrożenia. Użyj następującej procedury, aby monitorować stan wdrożenia sekwencji zadań.  

#### <a name="to-monitor-deployment-status"></a>Aby monitorować stan wdrożenia  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym Monitorowanie kliknij przycisk **Wdrożenia**.  

3.  Kliknij sekwencję zadań, dla której chcesz monitorować stan wdrożenia.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrożenie** kliknij przycisk **Wyświetl stan**.  

##  <a name="BKMK_TSReports"></a> Raporty wdrożenia systemu operacyjnego  
 Jest dostępnych wiele wstępnie zdefiniowanych raportów wdrożenia systemu operacyjnego. Są one podzielone na kilka kategorii i można ich używać do raportowania określonych informacji dotyczących migracji stanu i wdrożeń sekwencji zadań. Oprócz wstępnie skonfigurowanych raportów można również tworzyć niestandardowe raporty dotyczące aktualizacji oprogramowania w zależności od potrzeb danej organizacji. Aby uzyskać więcej informacji, zobacz [operacje i Obsługa raportowania](../../core/servers/manage/operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_MonitorContent"></a> Monitorowanie zawartości  
 Można monitorować zawartość w konsoli programu Configuration Manager, aby sprawdzić stan dla wszystkich typów pakietów w odniesieniu do powiązanych punktów dystrybucji. Może to dotyczyć między innymi stanu sprawdzania poprawności zawartości pakietu, stanu zawartości przypisanej do konkretnej grupy punktów dystrybucji, stanu zawartości przypisanej do punktu dystrybucji oraz stanu funkcji opcjonalnych poszczególnych punktów dystrybucji (sprawdzanie poprawności zawartości, środowiska PXE oraz multiemisji).  

###  <a name="BKMK_ContentStatus"></a> Monitorowanie stanu zawartości  
 Węzeł **Stan zawartości** w obszarze roboczym **Monitorowanie** zawiera informacje na temat pakietów zawartości. Można w nim wyświetlić ogólne informacje dotyczące pakietu, jego stanu dystrybucji oraz szczegółowe informacje o stanie pakietu. Aby wyświetlić stan zawartości, należy wykonać następujące czynności.  

#### <a name="to-monitor-content-status"></a>Aby monitorować stan zawartości  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym Monitorowanie rozwiń węzeł **Stan dystrybucji**, a następnie kliknij przycisk **Stan zawartości**. Są wyświetlane pakiety.  

3.  Wybierz pakiet, dla którego chcesz wyświetlić szczegółowe informacje o stanie.  

4.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie pakietu.  

###  <a name="BKMK_DPGroupStatus"></a> Stan grupy punktów dystrybucji  
 Węzeł **Stan grup punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje dotyczące grup punktów dystrybucji. Można w nim przejrzeć informacje ogólne dotyczące grupy punktów dystrybucji, na przykład stanu grupy punktów dystrybucji i poziom zgodności, a także szczegółowe informacje o stanie grupy punktów dystrybucji. Aby wyświetlić stan grupy punktów dystrybucji, należy wykonać następującą procedurę.  

#### <a name="to-monitor-distribution-point-group-status"></a>Aby monitorować stan grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym Monitorowanie rozwiń węzeł **Stan dystrybucji**, a następnie kliknij przycisk **Stan grup punktów dystrybucji**. Zostaną wyświetlone grupy punktów dystrybucji.  

3.  Wybierz grupę punktów dystrybucji, dla której chcesz wyświetlić szczegółowe informacje o stanie.  

4.  Na karcie **Narzędzia główne** kliknij przycisk **Wyświetl stan**. Zostaną wyświetlone szczegółowe informacje o stanie grupy punktów dystrybucji.  

###  <a name="BKMK_DPConfigStatus"></a> Stan konfiguracji punktów dystrybucji  
 Węzeł **Stan konfiguracji punktów dystrybucji** w obszarze roboczym **Monitorowanie** zawiera informacje o punkcie dystrybucji. Można w nim sprawdzić atrybuty włączone w punkcie dystrybucji, jak na przykład środowisko PXE, multiemisja lub sprawdzanie poprawności zawartości. Można również wyświetlić szczegółowe informacje o stanie punktu dystrybucji. Aby wyświetlić stan konfiguracji punktów dystrybucji, należy wykonać następującą procedurę.  

#### <a name="to-monitor-distribution-point-configuration-status"></a>Aby monitorować stan konfiguracji punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym Monitorowanie rozwiń węzeł **Stan dystrybucji**, a następnie kliknij przycisk **Stan konfiguracji punktów dystrybucji**. Zostaną wyświetlone punkty dystrybucji.  

3.  Wybierz punkt dystrybucji, dla którego mają być wyświetlone informacje o stanie punktu dystrybucji.  

4.  W okienku wyników kliknij kartę **Szczegóły** . Zostaną wyświetlone informacje o stanie punktu dystrybucji.  
