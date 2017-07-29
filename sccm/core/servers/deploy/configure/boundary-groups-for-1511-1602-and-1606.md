---
title: Grupy granic 1511, 1602 i 1606 | System Center Configuration Manager
description: "Za pomocą programu Configuration Manager w wersji 1511, 1602 i 1606 grup granic."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dec1e0d7-5864-43a8-9f56-413923b3914e
caps.latest.revision: 10
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 640cdc67f301a81a45bf27f95eb03cbc8754a9aa
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="boundary-groups-for-system-center-configuration-manager-version-1511-1602-and-1606"></a>Grupy granic programu System Center Configuration Manager wersji 1511, 1602 i 1606

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*
<!-- This topic drops from TOC with the release of version 1706 -->

Informacje przedstawione w tym temacie jest właściwy za pomocą grup granic w wersjach 1511, 1602, 1606 programu System Center Configuration Manager.
Jeśli używasz wersji 1610 lub nowszej, zobacz [konfigurowania grup granic](/sccm/core/servers/deploy/configure/boundary-groups) informacji o sposobie używania grupy granic przeprojektowane.  


##  <a name="BKMK_BoundaryGroups"></a> Boundary groups  
 Grupy granic tworzy się w celu logicznego pogrupowania powiązanych lokalizacji sieciowych (granic), aby ułatwić zarządzanie infrastrukturą. Przed użyciem grup granic należy do nich przypisać granice. Klienci używają konfiguracji grupy granic na potrzeby:  

-   Automatycznego przypisywania lokacji  

-   Lokalizacja zawartości  

-   Preferowane punkty

    Jeśli użyjesz preferowane punkty konieczne jest włączenie tej opcji dla hierarchii, a nie za pomocą konfigurację grupy granic. Zobacz *aby umożliwić użycie preferowane punkty* procedury w dalszej części tego tematu.  

Podczas konfigurowania grup granic należy dodać jedną lub więcej granic do grupy granic. Następnie skonfiguruj dodatkowe ustawienia używane przez klientów, którzy znajdują się w tych granicach.  

#### <a name="to-create-a-boundary-group"></a>Aby utworzyć grupę granic  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz grupę granicę**.  

3.  W **Utwórz grupę granicę** okno dialogowe Wybierz **ogólne** karcie, a następnie wprowadź **nazwa** dla tej grupy granic.  

4.  Wybierz **OK** Aby zapisać nową grupę granic.  

#### <a name="to-set-up-a-boundary-group"></a>Aby skonfigurować grupę granic  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Wybierz grupę granic, którą chcesz zmienić.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W **właściwości** okno dialogowe dla grupy granic wybierz **ogólne** kartę, aby zmienić granice, które są członkami tej grupy granic:  

    -   Aby dodać granice, wybierz **Dodaj**, zaznacz pole wyboru dla przynajmniej jednej granicy, a następnie wybierz **OK**.  

    -   Aby usunąć granicę, wybierz granicę, a następnie wybierz **usunąć**.  

5.  Wybierz **odwołania** kartę, aby zmienić przypisanie lokacji oraz konfigurację serwera systemu lokacji skojarzone:  

    -   Aby włączyć tej grupy granic używane przez klientów do przypisania lokacji, zaznacz pole wyboru dla **Użyj tej grupy granic dla przypisania lokacji**, a następnie wybierz lokację z **przypisana lokacja** pole listy rozwijanej.  

    -   Aby skonfigurować serwery systemu lokacji skojarzone z tą grupą granic:  

    1.  Wybierz **Dodaj**, a następnie zaznacz pole wyboru dla jednego lub więcej serwerów. Serwery zostaną dodane jako skojarzone serwery systemu lokacji dla tej grupy granic. Dostępne będą tylko serwery, na których zainstalowano obsługiwaną rolę systemu lokacji.  

        > [!NOTE]  
        >  Można wybrać dowolną kombinację dostępnych systemów lokacji z dowolnej lokacji w hierarchii. Wybrane systemy lokacji są wyświetlane na karcie **Systemy lokacji** we właściwościach wszystkich granic należących do tej grupy granic.  

    2.  Aby usunąć serwer z tej grupy granic, wybierz serwer, a następnie wybierz **usunąć**.  

        > [!NOTE]  
        >  Aby przerwać użycie tej grupy granic kojarzenia systemów lokacji, należy usunąć wszystkie serwery, które są wyświetlane jako serwery systemu lokacji skojarzone.  

    3.  Aby zmienić szybkość połączenia sieciowego dla serwera systemu lokacji dla tej grupy granic, wybierz serwer, a następnie wybierz **Zmień połączenie**.  

         Domyślnie szybkość połączenia dla każdego systemu lokacji jest **Fast**, ale można zmienić szybkość **wolno**. Szybkość połączenia sieciowego i konfiguracja wdrożenia określają, czy klient może pobierać zawartość z serwera.  

6.  Wybierz **OK** aby zamknąć właściwości grupy granic i zapisać konfigurację.  

#### <a name="to-associate-a-content-deployment-server-or-management-point-with-a-boundary-group"></a>Aby skojarzyć serwer rozmieszczania zawartości lub punkt zarządzania z grupą granic  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Wybierz grupę granic, którą chcesz zmienić.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W **właściwości** okno dialogowe dla grupy granic wybierz **odwołania** kartę.  

5.  W obszarze **wybierz serwery systemu lokacji**, wybierz **Dodaj**, zaznacz pole wyboru dla serwerów systemu lokacji, które chcesz skojarzyć z tą grupą granic, a następnie wybierz **OK**.  

6.  Wybierz **OK** aby zamknąć okno dialogowe i zapisać konfigurację grupy granic.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Aby włączyć korzystanie z preferowanych punktów zarządzania  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie na **Home** , wybierz **ustawienia hierarchii**.  

2.  Na **ogólne** na karcie **ustawienia hierarchii**, wybierz **klienci wolą używać punktów zarządzania określonych w grupach granic**.  

3.  Wybierz **OK** aby zamknąć okno dialogowe i zapisać konfigurację.  

#### <a name="to-set-up-a-fallback-site-for-automatic-site-assignment"></a>Aby skonfigurować lokację rezerwową do automatycznego przypisywania lokacji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **konfiguracja lokacji** >  **witryny**.  

2.  Na **Home** w karcie **witryny** grupy, wybierz **ustawienia hierarchii**.  

3.  Na **ogólne** kartę, zaznacz pole wyboru dla **Użyj lokacji rezerwowej**, a następnie wybierz lokację z **lokacji rezerwowej** listy rozwijanej.  

4.  Wybierz **OK** Aby zapisać konfigurację.  

 Poniższe sekcje zawierają dodatkowe informacje o konfiguracjach grupy granic.  

###  <a name="BKMK_BoundarySiteAssignment"></a> Informacje o przypisywaniu lokacji  
 Każda grupa granic z przypisaną lokacją można skonfigurować dla klientów.  

-   Nowo zainstalowany klient używający automatyczne przypisanie lokacji będzie dołączać do przypisanej lokacji grupy granic, zawierający bieżącą lokalizację sieciową klienta.  

-   Klient, który jest przypisany do lokacji nie zmienia jej przypisanie lokacji zmianie jego lokalizacji sieciowej klienta. Na przykład jeśli klient przejdzie do nowej lokalizacji sieciowej, która jest reprezentowana przez granicę w grupie granic z innym przypisaniem lokacji, przypisana lokacja klienta nie zostanie zmieniona.  

-   Kiedy funkcja odnajdowania systemu usługi Active Directory odnajdzie nowy zasób, informacje o sieci odnalezionego zasobu zostaną ocenione względem granic w grupach granic. Ten proces powoduje skojarzenie nowego zasobu z przypisaną lokacją w celu użycia przez metodę instalacji klienta w trybie wypychania.  

-   Gdy granicy do wielu grup granic, które mają przypisane różne lokacje, klientów losowo wybierz jedną z lokacji.  

-   Zmiany w lokacji przypisanej grupie granic dotyczą tylko nowe akcje przypisania lokacji. Klientów, które zostały wcześniej przypisani do lokacji nie są oceniane przypisania lokacji ponownie na podstawie zmian w konfiguracji grupy granic (lub do lokalizacji sieciowej).  

Aby uzyskać więcej informacji o przypisywaniu lokacji klienta, zobacz [za pomocą automatycznego przypisania lokacji dla komputerów](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

###  <a name="BKMK_BoundaryContentLocation"></a> Informacje o lokalizacji zawartości  
 Można skonfigurować każdą grupą granic z jednego lub więcej punktów dystrybucji i punktów migracji stanu i samych punktów dystrybucji i punktów migracji stanu można skojarzyć z różnymi grupami granic.  

-   **Podczas dystrybucji oprogramowania**klienci żądają lokalizacji na potrzeby wdrożenia zawartości. Menedżer konfiguracji wysyła klientowi listę punktów dystrybucji, które są skojarzone z każdą grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

-   **Podczas wdrażania systemu operacyjnego**, klient żąda lokacji do wysłania lub odebrania informacji o migracji stanu. Menedżer konfiguracji wysyła klientowi listę punktów migracji stanu, które są skojarzone z każdą grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

Dzięki temu klient wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  

###  <a name="BKMK_PreferredMP"></a> Informacje o preferowanych punktach zarządzania  
 Preferowane punkty pozwalają zidentyfikować punkt zarządzania skojarzony z jego bieżącej lokalizacji sieciowej (granicy) klienta.  

-   Klient próbuje użyć preferowanym punktem zarządzania z przypisanej mu lokacji przed używa punktu zarządzania z przypisanej mu lokacji, który nie jest skonfigurowany jako preferowany.  

-   Aby użyć tej opcji, należy ją włączyć w hierarchii i konfigurowanie grup granic w poszczególnych lokacjach głównych do uwzględnienia punkty zarządzania, które mogą być skojarzone z tej grupy granic granice skojarzone  

-   Podczas preferowane punkty są skonfigurowane, a klient organizuje listy zarządzania punktów, miejsca klienta zarządzania preferowanych punktów w górnej części listy punktów zarządzania przypisanej, w tym wszystkie punkty zarządzania w przypisanej lokacji klienta.  

> [!NOTE]  
>  Gdy klient przejdzie, takich jak kiedy komputer przenośny przechodzi do zdalnej lokalizacji biura i zmienia jej lokalizację sieciową może zostać użyty punkt zarządzania (lub punktu zarządzania serwera proxy) z lokalnej witryny w nowym położeniu przed próbuje użyć punktu zarządzania z przypisanej mu lokacji (w tym punkty zarządzania preferowanych).  Zobacz [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) uzyskać więcej informacji.  

###  <a name="BKMK_BoundaryOverlap"></a> Informacje o nakładaniu się granic  
 Program Configuration Manager obsługuje konfiguracje nakładających się granic dla lokalizacji zawartości:  

-   **Gdy klient zażąda zawartości**, a lokalizacja sieciowa klienta należy do różnych grup granic, program Configuration Manager wysyła klientowi listę wszystkich punktów dystrybucji z zawartością.  

-   **Gdy klient zażąda serwera, aby wysłać lub odebrać informacje o migracji stanu**, a lokalizacja sieciowa klienta należy do różnych grup granic, program Configuration Manager wysyła klientowi listę punktów migracji stanu skojarzonych z grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

Dzięki temu klient wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  

###  <a name="BKMK_BoudnaryNetworkSpeed"></a> Informacje o szybkości połączenia sieciowego  
 Szybkość połączenia sieciowego można ustawić dla każdego serwera systemu lokacji w grupie granic. To ustawienie dotyczy klientów, którzy łączą się z systemem lokacji, na podstawie konfiguracji tej grupy granic. Ten sam serwer systemu lokacji może mieć inną szybkość połączenia ustawioną dla różnych grup granic.  

 Domyślnie szybkość połączenia sieciowego jest równa **Fast**, ale można go zmienić **wolno**. Szybkość połączenia sieciowego i Konfiguracja wdrożenia Sprawdź, czy klient może pobierać zawartość z punktu dystrybucji, gdy klient jest skojarzona grupa granic.  

 Aby uzyskać więcej informacji o sposobie konfiguracji szybkość połączenia sieciowego wpływa na sposób pobierania zawartości klienci, zobacz [scenariusze lokalizacji źródła zawartości](../../../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

