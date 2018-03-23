---
title: 'Synchronizowanie danych programu Microsoft Operations Management Suite '
titleSuffix: Configuration Manager
description: Synchronizowanie danych z programu System Center Configuration Manager do programu Microsoft Operations Management Suite.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: df57255108d0e5e8b8f5e4e8d73a392c4cf2faae
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
#  <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Synchronizowanie danych z programu Configuration Manager do programu Microsoft Operations Management Suite

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz użyć **Kreator usług Azure** do skonfigurowania połączenia z programu Configuration Manager do usługi w chmurze Operations Management Suite (OMS). Począwszy od wersji 1706, kreator zastępuje poprzednie przepływy pracy w celu skonfigurowania tego połączenia. W przypadku wcześniejszych wersji, zobacz [synchronizowanie danych z programu Configuration Manager do programu Microsoft Operations Management Suite (1702 i starszych)](#Sync-data-from-Configuration-Manager-to-the-Microsoft-Operations-Management-Suite-(1702-and-earlier)).

-   Kreator służy do konfigurowania usługi w chmurze dla programu Configuration Manager, takich jak OMS, Microsoft Store dla firm i Azure Active Directory (Azure AD).  

-   Configuration Manager łączy się z usługą OMS dla funkcji, takich jak [analizy dzienników](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite), lub [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics).

## <a name="prerequisites-for-the-oms-connector"></a>Wymagania wstępne dotyczące łącznika OMS
Wymagania wstępne, aby skonfigurować połączenie z usługą OMS uległy zmianie od wymagań wstępnych [udokumentowane dla wersji Current Branch 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#prerequisites). Te informacje jest powtarzany w tym miejscu:  

-   Przed zainstalowaniem łącznika OMS w programie Configuration Manager, musisz podać programu Configuration Manager z uprawnieniami do OMS. W szczególności należy przyznać *dostępu współautora* Azure *grupy zasobów* zawierający obszar roboczy analizy dzienników OMS. Procedury przedstawione w tym celu są udokumentowane w zawartości analizy dzienników. Zobacz [Podaj programu Configuration Manager z uprawnieniami do OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) w dokumentacji pakietu OMS.

-   Łącznik pakietu OMS musi być zainstalowany na komputerze, który obsługuje [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

-   Musisz zainstalować program Microsoft Monitoring Agent dla OMS zainstalowany w punkcie połączenia usługi oraz łącznik OMS. Agent i łącznik pakietu OMS musi być skonfigurowana do używać tego samego **obszarem roboczym pakietu OMS**. Aby zainstalować agenta, zobacz [pobrać i zainstalować agenta](/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) w dokumentacji pakietu OMS.
-   Po zainstalowaniu łącznika i agenta, należy skonfigurować OMS używanie danych programu Configuration Manager. Aby to zrobić, w portalu OMS możesz [kolekcji programu Configuration Manager importu](/azure/log-analytics/log-analytics-sccm#import-collections).

## <a name="use-the-azure-services-wizard-to-configure-the-connection-to-oms"></a>Użyj kreatora usług Azure, aby skonfigurować połączenie z usługą OMS

1.  W konsoli przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **usług Azure**. Wybierz **Konfigurowanie usług Azure** z **Home** kartę na Wstążce, aby uruchomić **Kreator usług Azure**.

2.  Na **usług Azure** wybierz usługę w chmurze operację Management Suite. Podaj przyjazną nazwę dla **nazwy usługi Azure** i opcjonalny opis, a następnie kliknij przycisk **dalej**.

3.  Na **aplikacji** Określ środowisku platformy Azure (wersja zapoznawcza technical preview obsługuje tylko chmury publicznej). Następnie kliknij przycisk **Przeglądaj** można otworzyć okna aplikacji serwera.

4.  Wybierz aplikację sieci web:

    -   **Importuj**: Aby korzystać z aplikacji sieci web, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i dzierżawcy. Określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po **Sprawdź** informacji, kliknij przycisk **OK** aby kontynuować.   

    > [!NOTE]   
    > Po skonfigurowaniu OMS w tej wersji zapoznawczej OMS obsługuje tylko *zaimportować* funkcja dla aplikacji sieci web. Tworzenie nowej aplikacji sieci web nie jest obsługiwane. Podobnie nie można ponownie użyć istniejącej aplikacji dla pakietu OMS.

5.  Jeśli wykonano wszystkie inne procedury pomyślnie, następnie informacje w **konfiguracji połączenia OMS** ekranu będzie automatycznie wyświetlane na tej stronie. Informacje o ustawieniach połączenia ma być wyświetlany dla Twojego **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, i **obszar roboczy usługi Operations Management Suite**.

6.  Kreator łączy się z usługą OMS, korzystając z informacji podanych przez Ciebie danych wejściowych. Wybierz kolekcje urządzeń, które mają być synchronizowane z usługą OMS, a następnie kliknij przycisk **Dodaj**.

7.  Sprawdź ustawienia połączenia w **Podsumowanie** ekranu, a następnie wybierz **dalej**. **Postępu** ekranu przedstawia stan połączenia, a następnie należy **Complete**.

8.  Po zakończeniu działania kreatora, konsoli programu Configuration Manager pokazuje, że skonfigurowano **operacji Management Suite** jako **typu usługi w chmurze**.

## <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite-1702-and-earlier"></a>Synchronizowanie danych z programu Configuration Manager do programu Microsoft Operations Management Suite (1702 i starsze)


*Dotyczy: System Center Configuration Manager (1702 i poprzednie wersje)*

Można użyć łącznika programu Microsoft Operations Management Suite (OMS), na synchronizowanie danych, takich jak kolekcji programu System Center Configuration Manager do analizy dzienników OMS platformie Microsoft Azure. Łącznik powoduje, że dane z wdrożenia programu Configuration Manager jest widoczna w OMS.
> [!TIP]
> Począwszy od programu Configuration Manager 1802 OMS łącznik nie jest już funkcji wersji wstępnej. Aby dowiedzieć się więcej, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/pre-release-features).

Począwszy od wersji 1702, można użyć łącznika OMS nawiązać obszar roboczy OMS, który znajduje się w chmurze Microsoft Azure dla instytucji rządowych. Należy zmodyfikować plik konfiguracji, przed zainstalowaniem łącznika OMS. Zobacz [korzystania z łącznika OMS z chmury Azure dla instytucji rządowych](#fairfaxconfig) w tym artykule.

### <a name="prerequisites"></a>Wymagania wstępne
- Przed zainstalowaniem łącznika OMS w programie Configuration Manager, musisz podać programu Configuration Manager z uprawnieniami do OMS. W szczególności należy przyznać *dostępu współautora* Azure *grupy zasobów* zawierający obszar roboczy analizy dzienników OMS. Procedury przedstawione w tym celu są udokumentowane w zawartości analizy dzienników. Zobacz [Podaj programu Configuration Manager z uprawnieniami do OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) w dokumentacji pakietu OMS.

- Łącznik pakietu OMS musi być zainstalowany na komputerze, który obsługuje [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

  Jeśli nawiązano połączenie OMS autonomiczną lokacją główną i planowane jest dodanie centralnej lokacji administracyjnej do środowiska, należy usunąć bieżące połączenie i ponownie skonfigurować łącznik na nowej centralnej lokacji administracyjnej.

- Musisz zainstalować program Microsoft Monitoring Agent dla OMS zainstalowany w punkcie połączenia usługi oraz łącznik OMS.  Agent i łącznik pakietu OMS musi być skonfigurowana do używać tego samego **obszarem roboczym pakietu OMS**. Aby zainstalować agenta, zobacz [pobrać i zainstalować agenta](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) w dokumentacji pakietu OMS.

- Po zainstalowaniu łącznika i agenta, należy skonfigurować OMS używanie danych programu Configuration Manager.  Aby to zrobić, w portalu OMS możesz [kolekcji programu Configuration Manager importu](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections).



### <a name="install-the-oms-connector"></a>Instalowanie łącznika OMS  
1. W konsoli programu Configuration Manager, należy skonfigurować z [hierarchii w celu korzystania z funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features), a następnie Włącz użycie łącznika OMS.  
0
2. Następnie należy przejść do **administracji** > **usługi w chmurze** > **łącznik OMS**. Na wstążce kliknij przycisk "Utwórz połączenie pakietu Operations Management Suite." Ten krok powoduje otwarcie **połączenie Kreator operacji Management Suite**. Wybierz **dalej**.  


3.  Na **ogólne** upewnij się, że następujące informacje, a następnie wybierz **dalej**.  
  - Zarejestrowany Menedżer konfiguracji narzędzia do zarządzania "API sieci Web i/lub aplikacji sieci Web", a [identyfikator klienta z tej rejestracji](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).  
  - Utworzony klucz klienta dla zarejestrowanego narzędzia do zarządzania w usłudze Azure Active Directory.  

  - W portalu Azure, pod warunkiem aplikacji sieci web w zarejestrowany z uprawnieniami do OMS, zgodnie z opisem w [Podaj programu Configuration Manager z uprawnieniami do OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms).  

4.  Na **usługi Azure Active Directory** Skonfiguruj ustawienia połączenia z usługą OMS zapewniając Twojej **dzierżawy**, **identyfikator klienta**, i **klucza tajnego klienta**, a następnie wybierz pozycję **dalej**.  

5.  Na **konfiguracji połączenia OMS** Podaj ustawienia połączenia, wypełniając Twojej **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, i **obszar roboczy usługi Operations Management Suite**.  Obszar roboczy musi być zgodna obszaru roboczego, który jest skonfigurowany dla agenta zarządzania Microsoft zainstalowanego na punkt połączenia usługi.  

6.  Sprawdź ustawienia połączenia w **Podsumowanie** strony, a następnie wybierz **dalej**. **Postępu** strony wyświetlany jest stan połączenia należy następnie **Complete**.

Po połączeniu programu Configuration Manager z usługą OMS Dodaj lub usuń kolekcje, a wyświetlić właściwości połączenia OMS.

### <a name="verify-the-oms-connector-properties"></a>Sprawdź właściwości łącznika OMS
1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **usługi w chmurze**, a następnie wybierz **OMS łącznik** otworzyć **OMS Strona połączenia**.
2.  Na tej stronie istnieją dwie karty:
  - **Usługa Azure Active Directory:** 
  
     Ta karta przedstawia Twojej **dzierżawy**, **identyfikator klienta**, **wygaśnięcia klucza tajnego klienta**, i pozwala sprawdzić, Twój klucz tajny klienta utracił ważność.

  - **Właściwości połączenia OMS:**  

     Ta karta przedstawia Twojej **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, **obszar roboczy usługi Operations Management Suite**oraz listę **kolekcji urządzeń, które Operations Management Suite można uzyskać danych dla**. Użyj **Dodaj** i **Usuń** przycisków, aby zmodyfikować kolekcje, które są dozwolone.

### <a name="fairfaxconfig"> </a> Korzystania z łącznika OMS z chmury Azure dla instytucji rządowych


1.  Na każdym komputerze konsoli programu Configuration Manager zainstalowane należy edytować następujący plik konfiguracji do punktu w chmurze dla instytucji rządowych:  ***&lt;Ścieżka instalacji CM > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Zmiany:**

    Zmień wartość atrybutu Nazwa ustawienia *FairFaxArmResourceID* powinna być równa "https://management.usgovcloudapi.net/"

   - **Original:** &lt;setting name="FairFaxArmResourceId" serializeAs="String">   
      &lt;wartość > &lt; /value >   
      &lt;/ Ustawienia >

   - **Edycji:**     
      &lt;setting name="FairFaxArmResourceId" serializeAs="String"> &lt;value>https://management.usgovcloudapi.net/&lt;/value>  
      &lt;/ Ustawienia >

  Zmień wartość atrybutu Nazwa ustawienia *FairFaxAuthorityResource* powinna być równa "https://login.microsoftonline.us/"

  - **Oryginalne:** &lt;ustawienie name = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > &lt; /value >

    - **Edytowane:** &lt;ustawienie name = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość >https://login.microsoftonline.us/ &lt; /value >

2.  Po zapisaniu pliku z dwie zmiany ponownie uruchomić konsolę programu Configuration Manager na tym samym komputerze, a następnie użyj konsoli, aby zainstalować łącznik OMS. Aby zainstalować łącznik, skorzystaj z informacji w [synchronizowanie danych z programu Configuration Manager do programu Microsoft Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)i wybierz **obszar roboczy usługi Operations Management Suite** znajdujący się w chmurze Microsoft Azure dla instytucji rządowych.

3.  Po zainstalowaniu łącznika OMS połączenia do chmury dla instytucji rządowych jest dostępna, gdy używasz dowolnego konsoli, która jest połączona z lokacją.
