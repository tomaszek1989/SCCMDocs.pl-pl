---
title: Tworzenie kolekcji | Dokumentacja firmy Microsoft
description: "Utwórz kolekcje programu System Center Configuration Manager do zarządzania grupami użytkowników i urządzeń."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1401a35e-4312-4d3b-8ceb-0abbb10d4f05
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 44b4707b1a40624c51decf548d23ddd2164c5833
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-collections-in-system-center-configuration-manager"></a>Jak utworzyć kolekcje w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Kolekcje są grup użytkowników lub urządzeń. Użyj kolekcji zadań, takich jak zarządzanie aplikacjami, wdrażanie ustawień zgodności lub instalowanie aktualizacji oprogramowania. Za pomocą kolekcji można również zarządzać grupami ustawień klientów, a także używać ich na potrzeby funkcji administracji opartej na rolach do określania zasobów, do których użytkownik administracyjny może uzyskiwać dostęp. Configuration Manager zawiera kilka wbudowanych kolekcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).  

> [!NOTE]  
>  Kolekcja może zawierać użytkowników lub urządzeń, ale nie oba.  

 Poniższa tabela zawiera listę reguł, które można użyć do skonfigurowania elementów członkowskich kolekcji w programie Configuration Manager.  

|Typ reguły członkostwa|Więcej informacji|  
|--------------------------|----------------------|  
|Reguła bezpośrednia|Służy do wybierania użytkowników lub komputerów, które chcesz dodać do kolekcji. To członkostwo nie zmienia się, chyba że w przypadku usunięcia zasobu z programu Configuration Manager. Configuration Manager musi mieć odnalazł zasoby lub zostały one zaimportowane zasobów przed dodaniem ich do kolekcji reguły bezpośredniej. Kolekcje reguły bezpośredniej wymagają wykonania większej liczby czynności administracyjnych niż kolekcje reguły zapytania, ponieważ wymagają one ręczne wprowadzanie zmian.|  
|Reguła zapytania|Dynamiczne aktualizowanie członkostwa kolekcji na podstawie zapytania programu Configuration Manager uruchomioną zgodnie z harmonogramem. Możesz na przykład utworzyć kolekcję użytkowników będących członkami jednostki organizacyjnej Zasoby ludzkie w Usługach domenowych Active Directory. Ta kolekcja jest automatycznie aktualizowany, gdy nowi użytkownicy są dodane lub usunięte z jednostki organizacyjnej zasoby ludzkie.<br /><br /> Na przykład zapytań, które służy do tworzenia kolekcji, zobacz [jak tworzyć zapytania w programie System Center Configuration Manager](../../../../core/servers/manage/create-queries.md).|  
|Reguła dołączania kolekcji|Dołączanie elementów członkowskich innej kolekcji w kolekcji programu Configuration Manager, który członkostwo bieżącej kolekcji jest aktualizowane zgodnie z harmonogramem, jeśli dołączonej kolekcji ulegnie zmianie.<br /><br /> Do kolekcji można dodawać wiele reguł dołączania kolekcji.<br /> |  
|Reguła wykluczania kolekcji|Reguła wykluczania kolekcji umożliwia wykluczanie elementów członkowskich innej kolekcji z kolekcji programu Configuration Manager. Członkostwo bieżącej kolekcji jest aktualizowane zgodnie z harmonogramem, jeśli wykluczonej kolekcji ulegnie zmianie.<br /><br /> Do kolekcji można dodawać wiele reguł wykluczania kolekcji. Jeśli kolekcja zawiera zarówno kolekcji reguły dołączania i wykluczania kolekcji występuje konflikt, reguła wykluczania kolekcji ma priorytet.<br />              **Przykład:** Możesz utworzyć kolekcję z jedną regułą dołączania kolekcji i jedną regułą wykluczania kolekcji. Reguła dołączania kolekcji dotyczy kolekcji komputerów stacjonarnych firmy Dell. Kolekcja wykluczania dotyczy kolekcji komputerów, które mają mniej niż 4 GB pamięci RAM. Nowa kolekcja będzie zawierać komputery stacjonarne firmy Dell, które mają co najmniej 4 GB pamięci RAM.|  

 Użyj poniższych procedur ułatwiających tworzenie kolekcji w programie Configuration Manager. Możesz również zaimportować kolekcje, które zostały utworzone w tej lub innej lokacji programu Configuration Manager. Aby uzyskać informacje o tym, jak wyeksportować i zaimportować kolekcje, zobacz [Zarządzanie kolekcjami w programie System Center Configuration Manager](../../../../core/clients/manage/collections/manage-collections.md).  

 Aby uzyskać informacje o tworzeniu kolekcji dla komputerów z systemem Linux i UNIX, zobacz [jak zarządzać klientami dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md).  

##  <a name="BKMK_1"></a> Aby utworzyć kolekcję urządzeń  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcje urządzeń**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz kolekcję urządzeń**.  

4.  Na **ogólne** podaj **nazwa** i **komentarz**. Następnie w **kolekcja ograniczająca**, wybierz **Przeglądaj** aby wybrać kolekcję ograniczającą. Kolekcja będzie zawierać tylko elementy członkowskie z kolekcji ograniczającej.  

5.  Na **reguł członkostwa** strony **Kreatora tworzenia kolekcji urządzeń**w **Dodaj regułę** listy, wybierz typ reguły członkostwa, którego chcesz użyć dla tej kolekcji. Dla każdej kolekcji można skonfigurować wiele reguł.  

        
##### <a name="to-configure-a-direct-rule"></a>Aby skonfigurować regułę bezpośrednią  

1.  Na stronie **Wyszukiwanie zasobów** **Kreatora tworzenia reguły członkostwa bezpośredniego**podaj następujące informacje:  

-   **Klasa zasobów**: Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wskaż wybraną wartość **Zasób systemowy** , aby wyszukiwać dane spisu zwracane z komputerów klienckich, lub **Nieznany komputer** , aby dokonać wyboru spośród wartości zwróconych z nieznanych komputerów.  

-   **Nazwa atrybutu**: Wybierz atrybut skojarzony z wybraną klasą zasobów do wyszukiwania. Jeśli na przykład chcesz wybrać komputery według nazwy systemu NetBIOS, wybierz pozycję **Zasób systemowy** na liście **Klasa zasobów** i pozycję **Nazwa NetBIOS** na liście **Nazwa atrybutu** .  

-   **Wyklucz zasoby oznaczone jako przestarzałe** — Jeśli komputer kliencki jest oznaczony jako przestarzały, nie dołączaj tę wartość w wynikach wyszukiwania.  

-   **Wyklucz zasoby, które nie mają zainstalowanego klienta programu Configuration Manager** — nie będą wyświetlane w wynikach wyszukiwania.  

-   **Wartość:** Wprowadź wartość, dla której chcesz wyszukać nazwę wybranego atrybutu. Możesz użyć znaku procentu **%** jako symbolu wieloznacznego. Na przykład, aby wyszukać komputery, które mają NetBIOS nazwa zaczyna się od "M", wprowadź **M %** w tym polu.  

2.  Na **zasobów wybierz** Wybierz zasoby, które chcesz dodać do kolekcji w **zasobów** listy, a następnie wybierz pozycję **dalej**.  


##### <a name="to-configure-a-query-rule"></a>Aby skonfigurować regułę zapytania  

1.  W oknie dialogowym **Właściwości reguły zapytania** wprowadź następujące informacje:  

-   **Nazwa**: Określ unikatową nazwę.  

-   **Importuj instrukcję zapytania** -otwiera **Przeglądanie zapytań** okno dialogowe, w którym można wybrać [kwerendę programu Configuration Manager](../../../../core/servers/manage/create-queries.md) do użycia jako regułę zapytania dla kolekcji.   

-   **Klasa zasobu:** Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wskaż wybraną wartość typu **Zasób systemowy** , aby wyszukiwać dane spisu zwracane z komputerów klienckich, lub **Nieznany komputer** , aby dokonać wyboru spośród wartości zwróconych z nieznanych komputerów.  

-   **Edytuj instrukcję zapytania** -otwiera **właściwości instrukcji kwerendy** okno dialogowe, w którym można utworzyć zapytanie w celu użycia jako regułę dla kolekcji. Więcej informacji o zapytaniach znajduje się w temacie [Dokumentacja techniczna dotycząca zapytań w programie System Center Configuration Manager](../../../../core/servers/manage/queries-technical-reference.md).  

    
##### <a name="to-configure-an-include-collection-rule"></a>Aby skonfigurować regułę dołączania kolekcji  

W **Wybieranie kolekcji** oknie dialogowym Wybierz kolekcje, aby dołączyć do nowej kolekcji, a następnie wybierz pozycję **OK**.  

##### <a name="to-configure-an-exclude-collection-rule"></a>Aby skonfigurować regułę wykluczania kolekcji  

W **Wybieranie kolekcji** oknie dialogowym Wybierz kolekcje, aby wykluczyć z nowej kolekcji, a następnie wybierz pozycję **OK**.  

-   **Użyj aktualizacji przyrostowych dla tej kolekcji** — wybierz tę opcję, aby okresowo skanowanie w poszukiwaniu i zaktualizować tylko nowe lub zmienione zasobów od momentu poprzedniej oceny kolekcji, niezależnie od pełnej oceny kolekcji. Aktualizacje przyrostowe są wykonywane co 10 minut.  

> [!IMPORTANT]  
>  Kolekcje skonfigurowane za pomocą reguł zapytania korzystających z następujących klas nie obsługują aktualizacji przyrostowych:  
>   
> -   SMS_G_System_CollectedFile  
> -   SMS_G_System_LastSoftwareScan  
> -   SMS_G_System_AppClientState  
> -   SMS_G_System_DCMDeploymentState  
> -   SMS_G_System_DCMDeploymentErrorAssetDetails  
> -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
> -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
> -   SMS_G_User_DCMDeploymentCompliantAssetDetails (tylko kolekcje użytkowników)  
> -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails (tylko kolekcje użytkowników)  
> -   SMS_G_System_SoftwareUsageData  
> -   SMS_G_System_CI_ComplianceState  
> -   SMS_G_System_EndpointProtectionStatus  
> -   SMS_GH_System_*  
> -   SMS_GEH_System_*  

-   **Zaplanuj pełną aktualizację dla tej kolekcji** -zaplanować regularną pełną ocenę członkostwa w kolekcji.  

6.  Zakończ pracę z kreatorem, aby utworzyć nową kolekcję. Nowa kolekcja zostanie wyświetlona w węźle **Kolekcje urządzeń** obszaru roboczego **Zasoby i zgodność** .  

> [!NOTE]  
>  Należy odświeżyć lub ponownie załadować konsolę programu Configuration Manager, aby wyświetlić elementy kolekcji. Jednak elementów członkowskich nie pojawi się w kolekcji dopiero po pierwszej zaplanowanej aktualizacji lub ręcznym wybraniu **zaktualizuj członkostwo** dla kolekcji. Może upłynąć kilka minut na zakończenie aktualizowania kolekcji.  

##  <a name="BKMK_2"></a> Aby utworzyć kolekcję użytkowników  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcje użytkowników**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz kolekcję użytkowników**.  

4.  Na **ogólne** strony wizardprovide **nazwa** i **komentarz**. Następnie w **kolekcja ograniczająca**, wybierz **Przeglądaj** aby wybrać kolekcję ograniczającą. Kolekcja będzie zawierać tylko elementy członkowskie z kolekcji ograniczającej.  

5.  Na **reguł członkostwa** strony, podaj następujące informacje:  

    -   Na liście **Dodaj regułę** wybierz typ reguły członkostwa, której chcesz użyć dla tej kolekcji. Dla każdej kolekcji można skonfigurować wiele reguł.  

##### <a name="to-configure-a-direct-rule"></a>Aby skonfigurować regułę bezpośrednią  

1.  Na **wyszukiwanie zasobów** strony **bezpośredniego Kreatora tworzenia reguły członkostwa**, określ:  

-   **Klasa zasobów**: Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wybierz jedną z **zasób użytkownika** wartości, aby wyszukać informacje o użytkowniku zebrane przez program Configuration Manager lub **zasób grupy użytkowników** aby wyszukać informacje o grupie użytkowników zebrane przez program Configuration Manager.  

-   **Nazwa atrybutu**: Wybierz atrybut skojarzony z klasą zasobów, który chcesz wyszukać. Jeśli na przykład chcesz wybrać użytkowników według nazwy jednostki organizacyjnej, wybierz pozycję **Zasób użytkownika** na liście **Klasa zasobu** i pozycję **Nazwa jednostki organizacyjnej użytkownika** na liście **Nazwa atrybutu** .  

-   **Wartość:** Wprowadź wartość, który chcesz wyszukać. Możesz użyć znaku procentu **%** jako symbolu wieloznacznego. Na przykład, aby wyszukać użytkowników w jednostce Organizacyjnej Contoso, wprowadź **Contoso** w tym polu.  

2.  Na **zasobów wybierz** Wybierz zasoby, które chcesz dodać do kolekcji w **zasobów** listy.  

##### <a name="to-configure-a-query-rule"></a>Aby skonfigurować regułę zapytania  

1.  W **właściwości reguły zapytania** okna dialogowego, podaj:  

-   **Nazwa**: Unikatowa nazwa.  

-   **Importuj instrukcję zapytania** -otwiera **Przeglądanie zapytań** okno dialogowe, w którym można wybrać [kwerendę programu Configuration Manager](../../../../core/servers/manage/queries-technical-reference.md) do użycia jako regułę zapytania dla kolekcji.  

-   **Klasa zasobów**: Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wybierz jedną z **zasób użytkownika** wartości, aby wyszukać informacje o użytkowniku zebrane przez program Configuration Manager lub **zasób grupy użytkowników** aby wyszukać informacje o grupie użytkowników zebrane przez program Configuration Manager.  

-   **Edytuj instrukcję zapytania** -otwiera **właściwości instrukcji kwerendy** okno dialogowe, w którym można [tworzyć kwerendy](../../../../core/servers/manage/queries-technical-reference.md) do użycia jako regułę dla kolekcji.  

##### <a name="to-configure-an-include-collection-rule"></a>Aby skonfigurować regułę dołączania kolekcji  

W **Wybieranie kolekcji** oknie dialogowym Wybierz kolekcje, aby dołączyć do nowej kolekcji, a następnie wybierz pozycję **OK**.  

##### <a name="to-configure-an-exclude-collection-rule"></a>Aby skonfigurować regułę wykluczania kolekcji  

W **Wybieranie kolekcji** oknie dialogowym Wybierz kolekcje, aby wykluczyć z nowej kolekcji, a następnie wybierz pozycję **OK**.  


-   **Użyj aktualizacji przyrostowych dla tej kolekcji** — wybierz tę opcję, aby okresowo skanowanie w poszukiwaniu i zaktualizować tylko nowe lub zmienione zasobów od momentu poprzedniej oceny kolekcji, niezależnie od pełnej oceny kolekcji. Aktualizacje przyrostowe są wykonywane co 10 minut.  

> [!IMPORTANT]  
>  Kolekcje skonfigurowane za pomocą reguł zapytania korzystających z następujących klas nie obsługują aktualizacji przyrostowych:  
>   
> -   SMS_G_System_CollectedFile  
> -   SMS_G_System_LastSoftwareScan  
> -   SMS_G_System_AppClientState  
> -   SMS_G_System_DCMDeploymentState  
> -   SMS_G_System_DCMDeploymentErrorAssetDetails  
> -   SMS_G_System_DCMDeploymentCompliantAssetDetails  
> -   SMS_G_System_DCMDeploymentNonCompliantAssetDetails  
> -   SMS_G_User_DCMDeploymentCompliantAssetDetails (tylko kolekcje użytkowników)  
> -   SMS_G_User_DCMDeploymentNonCompliantAssetDetails (tylko kolekcje użytkowników)  
> -   SMS_G_System_SoftwareUsageData  
> -   SMS_G_System_CI_ComplianceState  
> -   SMS_G_System_EndpointProtectionStatus  
> -   SMS_GH_System_*  
> -   SMS_GEH_System_*  

-   **Zaplanuj pełną aktualizację dla tej kolekcji** -zaplanować regularną pełną ocenę członkostwa w kolekcji.  

6.  Ukończ pracę kreatora. Nowa kolekcja zostanie wyświetlona w węźle **Kolekcje użytkowników** obszaru roboczego **Zasoby i zgodność** .  

> [!NOTE]  
>  Należy odświeżyć lub ponownie załadować konsolę programu Configuration Manager, aby wyświetlić elementy kolekcji. Elementy członkowskie będą jednak widoczne w kolekcji dopiero po pierwszej zaplanowanej aktualizacji lub ręcznym wybraniu pozycji **Zaktualizuj członkostwo** dla kolekcji. Może upłynąć kilka minut na zakończenie aktualizowania kolekcji.  

##  <a name="BKMK_3"></a> Aby zaimportować kolekcję  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcje użytkowników** lub **kolekcje urządzeń**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Importuj kolekcje**.  

4.  Na **ogólne** strony **Kreatora importu kolekcji**, wybierz **dalej**.  

5.  Na **nazwa pliku MOF** wybierz pozycję **Przeglądaj** , a następnie przejdź do pliku MOF, który zawiera informacje o kolekcji do zaimportowania.  

    > [!NOTE]  
    >  Plik, który chcesz zaimportować należy wcześniej wyeksportować z witryny korzystającej tą samą wersję programu Configuration Manager. Aby uzyskać więcej informacji o eksportowaniu kolekcji, zobacz [Zarządzanie kolekcjami w programie System Center Configuration Manager](../../../../core/clients/manage/collections/manage-collections.md).  

6.  Zakończ pracę z kreatorem, aby zaimportować kolekcję. Nowa kolekcja zostanie wyświetlona w węźle **Kolekcje użytkowników** lub **Kolekcje urządzeń** obszaru roboczego **Zasoby i zgodność** . Odśwież lub ponownie załadować konsolę programu Configuration Manager, aby zobaczyć elementy członkowskie nowo zaimportowanej kolekcji.  
