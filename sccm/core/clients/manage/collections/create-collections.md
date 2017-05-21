---
title: Tworzenie kolekcji | Dokumentacja firmy Microsoft
description: "Tworzenie kolekcji w System Center Configuration Manager do zarządzania grupami użytkowników i urządzeń."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1401a35e-4312-4d3b-8ceb-0abbb10d4f05
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: dee63826d8e6100f5b8402952175106076585030
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-collections-in-system-center-configuration-manager"></a>Jak utworzyć kolekcje w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Kolekcje są grupami użytkowników lub urządzeń. Użyj kolekcji zadań, takich jak zarządzanie aplikacjami, wdrożenie ustawień zgodności lub instalowania aktualizacji oprogramowania. Za pomocą kolekcji można również zarządzać grupami ustawień klientów, a także używać ich na potrzeby funkcji administracji opartej na rolach do określania zasobów, do których użytkownik administracyjny może uzyskiwać dostęp. Menedżer konfiguracji zawiera kilka wbudowanych kolekcji. Aby uzyskać więcej informacji, zobacz [wprowadzenie do kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/introduction-to-collections.md).  

> [!NOTE]  
>  Kolekcja może zawierać użytkowników lub urządzeń, ale nie oba.  

 W poniższej tabeli wymieniono zasady używane do konfigurowania członków kolekcji w programie Configuration Manager.  

|Typ reguły członkostwa|Więcej informacji|  
|--------------------------|----------------------|  
|Reguła bezpośrednia|Służy do wybierania użytkowników lub komputery, które chcesz dodać do kolekcji. Członkostwo nie ulega zmianie, chyba że usunięcie zasobu z programu Configuration Manager. Configuration Manager zostały wykryte zasoby lub musi zaimportowano zasoby przed dodaniem ich do kolekcji reguły bezpośredniej. Kolekcje reguły bezpośredniej mają wyższe koszty administracyjne niż kolekcje reguł zapytania, ponieważ wymagają one ręczne zmiany.|  
|Reguła zapytania|Aktualizuj dynamicznie członkostwa w kolekcji na podstawie zapytania programu Configuration Manager uruchamiany zgodnie z harmonogramem. Możesz na przykład utworzyć kolekcję użytkowników będących członkami jednostki organizacyjnej Zasoby ludzkie w Usługach domenowych Active Directory. Ta kolekcja jest aktualizowana automatycznie, gdy nowi użytkownicy są dodane lub usunięte z jednostki organizacyjnej zasobów ludzkich.<br /><br /> Na przykład zapytań, które służy do tworzenia kolekcji, zobacz [tworzenie kwerend w programie System Center Configuration Manager](../../../../core/servers/manage/create-queries.md).|  
|Reguła dołączania kolekcji|Dołączyć członków innej kolekcji w kolekcji programu Configuration Manager przynależność do bieżącej kolekcji jest aktualizowany zgodnie z harmonogramem, jeśli zmieni się dołączone kolekcji.<br /><br /> Do kolekcji można dodawać wiele reguł dołączania kolekcji.<br /> |  
|Reguła wykluczania kolekcji|Zasadę pozwalają Wyklucz członków innej kolekcji z kolekcji programu Configuration Manager. Przynależność do bieżącej kolekcji zostanie zaktualizowany zgodnie z harmonogramem w przypadku zmiany wykluczonych kolekcji.<br /><br /> Do kolekcji można dodawać wiele reguł wykluczania kolekcji. Jeśli kolekcja zawiera zarówno kolekcji reguły dołączania i wykluczania kolekcji występuje konflikt, pierwszeństwo ma zasadę.<br />              **Przykład:** Tworzenie kolekcji, która zawiera jedną zasadę zbierania danych i jedną zasadę. Reguła dołączania kolekcji dotyczy kolekcji komputerów stacjonarnych firmy Dell. Kolekcja wykluczania dotyczy kolekcji komputerów, które mają mniej niż 4 GB pamięci RAM. Nowa kolekcja będzie zawierać komputery stacjonarne firmy Dell, które mają co najmniej 4 GB pamięci RAM.|  

 Użyj poniższych procedur ułatwiających tworzenie kolekcji w programie Configuration Manager. Można także zaimportować kolekcje, które zostały utworzone w tej lub innej lokacji programu Configuration Manager. Informacje o sposobie eksportowania i importowania kolekcji, zobacz [Zarządzanie kolekcje w programie System Center Configuration Manager](../../../../core/clients/manage/collections/manage-collections.md).  

 Informacje o tworzeniu kolekcje dla komputerów z systemem Linux i UNIX, zobacz [jak zarządzać klientami dla serwerów Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md).  

##  <a name="BKMK_1"></a> Aby utworzyć kolekcję urządzeń  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcji urządzeń**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz kolekcję urządzeń**.  

4.  Na **ogólne** Strony zapewniają **nazwa** i **komentarz**. Następnie w **ograniczanie kolekcji**, wybierz **Przeglądaj** aby wybrać kolekcję ograniczającą. Kolekcja będzie zawierać tylko elementy członkowskie z kolekcji ograniczającej.  

5.  Na **reguł członkostwa** strony **kreatorze tworzenia kolekcji urządzeń**w **Dodaj regułę** , wybierz typ reguły członkostwa, którego chcesz używać dla tej kolekcji. Dla każdej kolekcji można skonfigurować wiele reguł.  

        
        ##### To configure a direct rule  

        1.  Na stronie **Wyszukiwanie zasobów** **Kreatora tworzenia reguły członkostwa bezpośredniego**podaj następujące informacje:  

            -   **Klasa zasobów**: Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wskaż wybraną wartość **Zasób systemowy** , aby wyszukiwać dane spisu zwracane z komputerów klienckich, lub **Nieznany komputer** , aby dokonać wyboru spośród wartości zwróconych z nieznanych komputerów.  

            -   **Nazwa atrybutu**: Wybierz atrybut skojarzone z klasą wybrany zasób, który chcesz wyszukać. Jeśli na przykład chcesz wybrać komputery według nazwy systemu NetBIOS, wybierz pozycję **Zasób systemowy** na liście **Klasa zasobów** i pozycję **Nazwa NetBIOS** na liście **Nazwa atrybutu** .  

            -   **Wyklucz zasoby oznaczone jako przestarzałe** — Jeśli komputer kliencki jest oznaczony jako przestarzały nie zawierają tej wartości w wynikach wyszukiwania.  

            -   **Wyklucz zasoby, które nie mają zainstalowanego klienta programu Configuration Manager** -nie będą wyświetlane w wynikach wyszukiwania.  

            -   **Wartość:** Wprowadź wartość, dla której chcesz wyszukać nazwę wybranego atrybutu. Możesz użyć znaku procentu **%** jako symbolu wieloznacznego. Na przykład, aby wyszukać komputerów NetBIOS Nazwa rozpoczynający się od "M", wprowadź **M %** w tym polu.  

        2.  Na **Wybieranie zasobów** Wybierz zasoby, które chcesz dodać do kolekcji w **zasobów** , a następnie wybierz **dalej**.  


        ##### To configure a query rule  

        1.  W oknie dialogowym **Właściwości reguły zapytania** wprowadź następujące informacje:  

            -   **Nazwa**: Określ unikatową nazwę.  

            -   **Importuj instrukcji kwerendy** -otwiera **Przeglądaj kwerendy** okno dialogowe, w którym można wybrać [kwerendę programu Configuration Manager](../../../../core/servers/manage/create-queries.md) do użycia jako zasadę kwerendy dla kolekcji.   

            -   **Klasa zasobów:** Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wskaż wybraną wartość typu **Zasób systemowy** , aby wyszukiwać dane spisu zwracane z komputerów klienckich, lub **Nieznany komputer** , aby dokonać wyboru spośród wartości zwróconych z nieznanych komputerów.  

            -   **Edytuj instrukcji kwerendy** -otwiera **właściwości instrukcji kwerendy** okno dialogowe, w którym mogą tworzyć kwerendy do użycia jako zasady zbierania. Więcej informacji o zapytaniach znajduje się w temacie [Dokumentacja techniczna dotycząca zapytań w programie System Center Configuration Manager](../../../../core/servers/manage/queries-technical-reference.md).  

    
        ##### To configure an include collection rule  

        In the **Select Collections** dialog box, select the collections you want to include in the new collection, then choose **OK**.  

        ##### To configure an exclude collection rule  

        In the **Select Collections** dialog box, select the collections you want to exclude from the new collection, then choose **OK**.  

    -   **Użyj aktualizacji przyrostowych dla tej kolekcji** — wybierz tę opcję, aby okresowo skanowania w poszukiwaniu i zaktualizować tylko nowe lub zmienione zasobów od momentu poprzedniej oceny kolekcji, niezależnie od pełnej oceny kolekcji. Aktualizacje przyrostowe są wykonywane co 10 minut.  

        > [!IMPORTANT]  
        >  Kolekcje skonfigurowane za pomocą reguł zapytania korzystających z następujących klas nie obsługują aktualizacji przyrostowych:  
        >   
        >  -   SMS_G_System_CollectedFile  
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

    -   **Zaplanowania pełnej aktualizacji dla tej kolekcji** -zaplanować regularne pełnej oceny członkostwa kolekcji.  

6.  Zakończ pracę z kreatorem, aby utworzyć nową kolekcję. Nowa kolekcja zostanie wyświetlona w węźle **Kolekcje urządzeń** obszaru roboczego **Zasoby i zgodność** .  

> [!NOTE]  
>  Należy odświeżyć lub Załaduj ponownie konsolę programu Configuration Manager, aby zobaczyć członków kolekcji. Jednak elementy członkowskie nie pojawi się w kolekcji dopiero po pierwszym zaplanowanych aktualizacji lub ręcznie wybierz **członkostwa aktualizacji** dla kolekcji. Może potrwać kilka minut na ukończenie aktualizacji kolekcji.  

##  <a name="BKMK_2"></a> Aby utworzyć kolekcję użytkowników  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcji użytkowników**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **tworzenia kolekcji użytkowników**.  

4.  Na **ogólne** strony wizardprovide **nazwa** i **komentarz**. Następnie w **ograniczanie kolekcji**, wybierz **Przeglądaj** aby wybrać kolekcję ograniczającą. Kolekcja będzie zawierać tylko elementy członkowskie z kolekcji ograniczającej.  

5.  Na **reguł członkostwa** strony, podaj następujące informacje:  

    -   Na liście **Dodaj regułę** wybierz typ reguły członkostwa, której chcesz użyć dla tej kolekcji. Dla każdej kolekcji można skonfigurować wiele reguł.  

         ##### <a name="to-configure-a-direct-rule"></a>Aby skonfigurować regułę bezpośrednią  

        1.  Na **wyszukiwanie zasobów** strony **kreatora reguły członkostwa bezpośredniego tworzenia**, określ:  

            -   **Klasa zasobów**: Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wybierz jedną z **zasobów użytkownika** wartości, aby wyszukać użytkownika informacje zebrane przez program Configuration Manager lub **zasobów grupy użytkowników** wyszukiwania użytkownika grupy informacji zbieranych przez program Configuration Manager.  

            -   **Nazwa atrybutu**: Wybierz atrybut skojarzone z klasą zasobu, który chcesz wyszukać. Jeśli na przykład chcesz wybrać użytkowników według nazwy jednostki organizacyjnej, wybierz pozycję **Zasób użytkownika** na liście **Klasa zasobu** i pozycję **Nazwa jednostki organizacyjnej użytkownika** na liście **Nazwa atrybutu** .  

            -   **Wartość:** Wprowadź wartość, która ma być wyszukiwany. Możesz użyć znaku procentu **%** jako symbolu wieloznacznego. Na przykład, aby wyszukać użytkowników w jednostce Organizacyjnej Contoso, wprowadź **Contoso** w tym polu.  

        2.  Na **Wybieranie zasobów** Wybierz zasoby, które chcesz dodać do kolekcji w **zasoby** listy.  

        ##### <a name="to-configure-a-query-rule"></a>Aby skonfigurować regułę zapytania  

        1.  W **właściwości reguły kwerendy** okno dialogowe, zawierają:  

            -   **Nazwa**: Unikatowa nazwa.  

            -   **Importuj instrukcji kwerendy** -otwiera **Przeglądaj kwerendy** okno dialogowe, w którym można wybrać [kwerendę programu Configuration Manager](../../../../core/servers/manage/queries-technical-reference.md) do użycia jako zasadę kwerendy dla kolekcji.  

            -   **Klasa zasobów**: Wybierz typ zasobu, który chcesz wyszukać i dodać do kolekcji. Wybierz jedną z **zasobów użytkownika** wartości, aby wyszukać użytkownika informacje zebrane przez program Configuration Manager lub **zasobów grupy użytkowników** wyszukiwania użytkownika grupy informacji zbieranych przez program Configuration Manager.  

            -   **Edytuj instrukcji kwerendy** -otwiera **właściwości instrukcji kwerendy** okno dialogowe, w którym można [tworzyć kwerendy](../../../../core/servers/manage/queries-technical-reference.md) do użycia jako reguły dla kolekcji.  

        ##### <a name="to-configure-an-include-collection-rule"></a>Aby skonfigurować regułę dołączania kolekcji  

        W **wybierz kolekcje** okno dialogowe Wybierz kolekcje, aby dołączyć do nowej kolekcji, a następnie wybierz **OK**.  

        ##### <a name="to-configure-an-exclude-collection-rule"></a>Aby skonfigurować regułę wykluczania kolekcji  

        W **wybierz kolekcje** okno dialogowe Wybierz kolekcje, aby wykluczyć z nową kolekcję, a następnie wybierz **OK**.  


    -   **Użyj aktualizacji przyrostowych dla tej kolekcji** — wybierz tę opcję, aby okresowo skanowania w poszukiwaniu i zaktualizować tylko nowe lub zmienione zasobów od momentu poprzedniej oceny kolekcji, niezależnie od pełnej oceny kolekcji. Aktualizacje przyrostowe są wykonywane co 10 minut.  

        > [!IMPORTANT]  
        >  Kolekcje skonfigurowane za pomocą reguł zapytania korzystających z następujących klas nie obsługują aktualizacji przyrostowych:  
        >   
        >  -   SMS_G_System_CollectedFile  
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

    -   **Zaplanowania pełnej aktualizacji dla tej kolekcji** -zaplanować regularne pełnej oceny członkostwa kolekcji.  

6.  Ukończ pracę kreatora. Nowa kolekcja zostanie wyświetlona w węźle **Kolekcje użytkowników** obszaru roboczego **Zasoby i zgodność** .  

> [!NOTE]  
>  Należy odświeżyć lub Załaduj ponownie konsolę programu Configuration Manager, aby zobaczyć członków kolekcji. Elementy członkowskie będą jednak widoczne w kolekcji dopiero po pierwszej zaplanowanej aktualizacji lub ręcznym wybraniu pozycji **Zaktualizuj członkostwo** dla kolekcji. Może potrwać kilka minut na ukończenie aktualizacji kolekcji.  

##  <a name="BKMK_3"></a> Aby zaimportować kolekcję  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcji użytkowników** lub **kolekcji urządzeń**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **importu kolekcji**.  

4.  Na **ogólne** strony **Kreatora importu kolekcji**, wybierz **dalej**.  

5.  Na **nazwa pliku MOF** wybierz **Przeglądaj** i przejdź do pliku MOF, który zawiera informacje kolekcji do zaimportowania.  

    > [!NOTE]  
    >  Plik, który chcesz zaimportować należy wyeksportować z zainstalowaną tę samą wersję programu Configuration Manager w tej lokacji. Aby uzyskać więcej informacji o eksportowaniu kolekcji, zobacz [Zarządzanie kolekcje w programie System Center Configuration Manager](../../../../core/clients/manage/collections/manage-collections.md).  

6.  Zakończ pracę z kreatorem, aby zaimportować kolekcję. Nowa kolekcja zostanie wyświetlona w węźle **Kolekcje użytkowników** lub **Kolekcje urządzeń** obszaru roboczego **Zasoby i zgodność** . Odśwież lub ponownie załadować konsoli programu Configuration Manager, aby wyświetlić członków kolekcji dla nowo zaimportowany kolekcji.  

