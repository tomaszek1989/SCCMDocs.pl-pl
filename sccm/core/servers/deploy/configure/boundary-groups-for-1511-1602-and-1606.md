---
title: Grupy granic 1511, 1602 i 1606
titleSuffix: Configuration Manager
description: "Za pomocą programu Configuration Manager w wersji 1511, 1602 i 1606 grup granic."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dec1e0d7-5864-43a8-9f56-413923b3914e
caps.latest.revision: "10"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: fdc23a24bae43e3196bededf23a66ab2325f2c75
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="boundary-groups-for-system-center-configuration-manager-version-1511-1602-and-1606"></a>Grupy granic programu System Center Configuration Manager w wersji 1511, 1602 i 1606

*Dotyczy: Program System Center Configuration Manager (Current Branch)*
<!-- This topic drops from TOC with the release of version 1706 -->

Informacje przedstawione w tym temacie dotyczy za pomocą grup granic z wersji 1511, 1602 i 1606 programu System Center Configuration Manager.
Jeśli używasz wersji 1610 lub nowszej, zobacz [konfigurowania grup granic](/sccm/core/servers/deploy/configure/boundary-groups) informacji o sposobie używania grupy granic przeprojektowana.  


##  <a name="BKMK_BoundaryGroups"></a> Boundary groups  
 Grupy granic tworzy się w celu logicznego pogrupowania powiązanych lokalizacji sieciowych (granic), aby ułatwić zarządzanie infrastrukturą. Przed użyciem grup granic należy do nich przypisać granice. Klienci używają konfiguracji grupy granic na potrzeby:  

-   Automatycznego przypisywania lokacji  

-   Lokalizacja zawartości  

-   Preferowane punkty zarządzania

    Jeśli korzystasz z preferowanych punktów zarządzania, należy włączyć tę opcję dla hierarchii, a nie za pomocą konfiguracji grupy granic. Zobacz *umożliwia korzystanie z preferowanych punktów zarządzania* procedury w dalszej części tego tematu.  

Podczas konfigurowania grup granic należy dodać co najmniej jedną granicę do grupy granic. Można następnie skonfigurować dodatkowe ustawienia używane przez klientów, które znajdują się w tych granicach.  

#### <a name="to-create-a-boundary-group"></a>Aby utworzyć grupę granic  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz grupę granicę**.  

3.  W **Utwórz grupę granicę** oknie dialogowym wybierz **ogólne** karcie, a następnie wprowadź **nazwa** dla tej grupy granic.  

4.  Wybierz **OK** Aby zapisać nową grupę granic.  

#### <a name="to-set-up-a-boundary-group"></a>Aby skonfigurować grupę granic  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Wybierz grupę granic, która ma zostać zmieniony.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W **właściwości** okno dialogowe dla grupy granic, wybierz **ogólne** kartę, aby zmieniać granice obszarów, które są członkami tej grupy granic:  

    -   Aby dodać granice, należy wybrać **Dodaj**, zaznacz pole wyboru dla przynajmniej jednej granicy, a następnie wybierz **OK**.  

    -   Aby usunąć granicę, wybierz granicę, a następnie wybierz pozycję **Usuń**.  

5.  Wybierz **odwołania** kartę, aby zmienić przypisanie lokacji i konfiguracji serwera systemu lokacji skojarzone:  

    -   Aby włączyć tej grupy granic do użycia przez klientów do przypisania lokacji, zaznacz pole wyboru **Użyj tej grupy granic do przypisania lokacji**, a następnie wybierz lokację z **przypisana lokacja** pole listy rozwijanej.  

    -   Aby skonfigurować serwery systemu lokacji dostępne, które są skojarzone z tą grupą granic:  

    1.  Wybierz **Dodaj**, a następnie zaznacz pole wyboru dla jednego lub więcej serwerów. Serwery zostaną dodane jako skojarzone serwery systemu lokacji dla tej grupy granic. Dostępne będą tylko serwery, na których zainstalowano obsługiwaną rolę systemu lokacji.  

        > [!NOTE]  
        >  Można wybrać dowolną kombinację dostępnych systemów lokacji z dowolnej lokacji w hierarchii. Wybrane systemy lokacji są wyświetlane na karcie **Systemy lokacji** we właściwościach wszystkich granic należących do tej grupy granic.  

    2.  Aby usunąć serwer z tą grupą granic, wybierz serwer, a następnie wybierz **Usuń**.  

        > [!NOTE]  
        >  Aby przerwać użycie tej grupy granic do kojarzenia systemów lokacji, należy usunąć wszystkie serwery, które są wyświetlane jako skojarzone serwery systemu lokacji.  

    3.  Aby zmienić szybkość połączenia sieciowego dla serwera systemu lokacji dla tej grupy granic, wybierz serwer, a następnie wybierz **Zmień połączenie**.  

         Domyślnie szybkość połączenia dla każdego systemu lokacji jest **Fast**, ale można ją zmienić szybkość **wolno**. Szybkość połączenia sieciowego i konfiguracja wdrożenia określają, czy klient może pobierać zawartość z serwera.  

6.  Wybierz **OK** aby zamknąć właściwości grupy granic i zapisać konfigurację.  

#### <a name="to-associate-a-content-deployment-server-or-management-point-with-a-boundary-group"></a>Aby skojarzyć serwer rozmieszczania zawartości lub punkt zarządzania z grupą granic  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **Konfiguracja hierarchii** >  **grup granic**.  

2.  Wybierz grupę granic, która ma zostać zmieniony.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W **właściwości** okno dialogowe dla grupy granic, wybierz **odwołania** kartę.  

5.  W obszarze **wybierz serwery systemu lokacji**, wybierz **Dodaj**, zaznacz pole wyboru dla serwerów systemu lokacji, które chcesz skojarzyć z tą grupą granic, a następnie wybierz pozycję **OK**.  

6.  Wybierz **OK** aby zamknąć okno dialogowe i zapisać konfigurację grupy granic.  

#### <a name="to-enable-use-of-preferred-management-points"></a>Aby włączyć korzystanie z preferowanych punktów zarządzania  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny**, a następnie na **Home** , wybierz pozycję **ustawienia hierarchii**.  

2.  Na **ogólne** karcie **ustawienia hierarchii**, wybierz **klienci wolą używać punktów zarządzania określonych w grupach granic**.  

3.  Wybierz **OK** aby zamknąć okno dialogowe i zapisać konfigurację.  

#### <a name="to-set-up-a-fallback-site-for-automatic-site-assignment"></a>Do konfigurowania lokacji rezerwowej w celu automatycznego przypisania lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** >  **witryny**.  

2.  Na **Home** karcie **witryny** grupy, wybierz **ustawienia hierarchii**.  

3.  Na **ogólne** karcie, zaznacz pole wyboru dla **Użyj lokacji rezerwowej**, a następnie wybierz lokację z **lokacji rezerwowej** listy rozwijanej.  

4.  Wybierz **OK** Aby zapisać konfigurację.  

 Poniższe sekcje zawierają dodatkowe informacje o konfiguracjach grupy granic.  

###  <a name="BKMK_BoundarySiteAssignment"></a> Informacje o przypisywaniu lokacji  
 Każda grupa granic z przypisaną lokację można skonfigurować dla klientów.  

-   Nowo zainstalowanego klienta, który używa automatycznego przypisania lokacji będzie dołączać do przypisanej lokacji w grupie granic zawierającej bieżącą lokalizację sieciową klienta.  

-   Gdy klient zmienia lokalizację sieciową klienta, który jest przypisany do lokacji nie zmienia przypisania lokacji. Na przykład jeśli klient przejdzie do nowej lokalizacji sieciowej, która jest reprezentowana przez granicę w grupie granic z innym przypisaniem lokacji, przypisana lokacja klienta pozostanie niezmieniona.  

-   Kiedy funkcja odnajdowania systemu usługi Active Directory odnajdzie nowy zasób, informacje o sieci odnalezionego zasobu zostaną ocenione względem granic w grupach granic. Ten proces powoduje skojarzenie nowego zasobu z przypisaną lokacją w celu użycia przez metodę instalacji klienta w trybie wypychania.  

-   Gdy granicy do wielu grup granic, które mają przypisane różne lokacje, klientów losowo wybierać jedną z lokacji.  

-   Zmiany lokacji przypisanej grupie granic dotyczą tylko nowych akcji przypisania lokacji. Klientów, które zostały uprzednio przypisane do lokacji nie oceniają przypisania lokacji ponownie na podstawie zmian w konfiguracji grupy granic (lub do lokalizacji sieciowej).  

Aby uzyskać więcej informacji o przypisywaniu lokacji klienta, zobacz [przy użyciu automatycznego przypisania lokacji komputerów](../../../../core/clients/deploy/assign-clients-to-a-site.md#BKMK_AutomaticAssignment) w [jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../../core/clients/deploy/assign-clients-to-a-site.md).  

###  <a name="BKMK_BoundaryContentLocation"></a> Informacje o lokalizacji zawartości  
 Możesz skonfigurować każdą grupą granic, z jedną lub więcej punktów dystrybucji i punktów migracji stanu, a same punkty dystrybucji i punktów migracji stanu można skojarzyć z wieloma grupami granic.  

-   **Podczas dystrybucji oprogramowania**klienci żądają lokalizacji na potrzeby wdrożenia zawartości. Menedżer konfiguracji wysyła klientowi listę punktów dystrybucji, które są skojarzone z każdą grupą granic, co obejmuje także bieżącą lokalizację sieciową klienta.  

-   **Podczas wdrażania systemu operacyjnego**, klienci żądają lokalizacji do wysłania lub odebrania informacji o migracji stanu. Menedżer konfiguracji wysyła klientowi listę punktów migracji stanu, które są skojarzone z każdą grupą granic, co obejmuje także bieżącą lokalizację sieciową klienta.  

Dzięki temu klient wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  

###  <a name="BKMK_PreferredMP"></a> Informacje o preferowanych punktach zarządzania  
 Preferowane punkty zarządzania umożliwiają klienta, punkt zarządzania skojarzony z ich bieżącą lokalizacją sieciową (granicą).  

-   Klient próbuje użyć preferowanego punktu zarządzania z przypisanej lokacji, przed użyciem punktu zarządzania z przypisanej lokacji, który nie jest skonfigurowany jako preferowane.  

-   Aby użyć tej opcji, należy ją włączyć w hierarchii i skonfigurować grupy granic w poszczególnych lokacjach głównych w celu uwzględnienia punktów zarządzania, które powinny być skojarzone ze skojarzonymi granicami tej grupy granic  

-   Gdy preferowane punkty zarządzania są skonfigurowane, a klient organizuje swoją listę zarządzania punktów, miejsca klienta zarządzania preferowanych punktów na początku listy przypisanych punktów zarządzania, zawierającej wszystkie punkty zarządzania z przypisanej lokacji klienta.  

> [!NOTE]  
>  Gdy klient przemieszcza, takie jak kiedy komputer przenośny przemieści się do lokalizacji biura zdalnego i zmienia lokalizację sieciową, on może używać punktu zarządzania (lub punktu zarządzania serwera proxy) z lokacji lokalnej w nowej lokalizacji przed próbą użycia punktu zarządzania z przypisanej lokacji (która obejmuje preferowane punkty zarządzania).  Zobacz [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) Aby uzyskać więcej informacji.  

###  <a name="BKMK_BoundaryOverlap"></a> Informacje o nakładaniu się granic  
 Program Configuration Manager obsługuje nakładających się granic konfiguracje lokalizacji zawartości:  

-   **Gdy klient żąda zawartości**, a lokalizacja sieciowa klienta należy do wielu grup granic, programu Configuration Manager wysyła klientowi listę wszystkich punktów dystrybucji zawierających daną zawartość.  

-   **Gdy klient żąda serwera, aby wysłać lub odebrać informacje o migracji stanu**, a lokalizacja sieciowa klienta należy do wielu grup granic, programu Configuration Manager wysyła klientowi listę punktów migracji stanu skojarzonych z grupą granic zawierającą bieżącą lokalizację sieciową klienta.  

Dzięki temu klient wybranie najbliższego serwera, z którego można przetransferować zawartość lub informacje o migracji stanu.  

###  <a name="BKMK_BoudnaryNetworkSpeed"></a> Informacje o szybkości połączenia sieciowego  
 Szybkość połączenia sieciowego można ustawić dla każdego serwera systemu lokacji w grupie granic. To ustawienie dotyczy klientów nawiązujących połączenie z systemu lokacji na podstawie konfiguracji tej grupy granic. Ten sam serwer systemu lokacji może mieć inną szybkość połączenia ustawioną dla różnych grup granic.  

 Domyślnie szybkość połączenia sieciowego jest ustawiona **Fast**, ale można go zmienić **wolno**. Szybkość połączenia sieciowego oraz konfiguracji wdrożenia Sprawdź, czy klient może pobierać zawartość z punktu dystrybucji zostanie skojarzona grupa granic.  

 Aby uzyskać więcej informacji o jak konfiguracja szybkości połączenia sieciowego wpływa na sposób pobierania zawartości przez klientów, zobacz [scenariusze lokalizacji źródła zawartości](../../../../core/plan-design/hierarchy/content-source-location-scenarios.md).  
