---
title: Konfigurowanie usług platformy Azure
titleSuffix: Configuration Manager
description: Połącz środowiska programu Configuration Manager z usługami Azure do zarządzania chmurą, gotowości do uaktualnienia, Microsoft Store dla firm i Operations Management Suite.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a26a653e-17aa-43eb-ab36-0e36c7d29f49
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: b86c73f3f5662a00ca0b7f80b0c785c37aff0b1a
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Konfigurowanie usług platformy Azure do użytku z programem Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj **Kreator usług Azure** w celu uproszczenia procesu konfigurowania usług w chmurze Azure używane z programem Configuration Manager. Ten kreator zapewnia typowych konfiguracji za pomocą rejestracji aplikacji sieci web w usłudze Azure Active Directory (Azure AD). Te aplikacje, podaj szczegóły subskrypcji i konfiguracji i uwierzytelniania komunikacji z usługą Azure AD. Aplikacja zastępuje wprowadzania tych informacji każdorazowo, że zostało skonfigurowane do nowego składnika programu Configuration Manager lub usługi platformy Azure.



## <a name="available-services"></a>Dostępne usługi

Skonfiguruj następujących usług platformy Azure za pomocą tego kreatora:  

-   **Chmury zarządzania**: Usługa ta umożliwia lokacji i klientów do uwierzytelniania przy użyciu usługi Azure AD. Tego uwierzytelniania program inne scenariusze, takie jak:  

    - [Zainstaluj i przypisz przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10](/sccm/core/clients/deploy/deploy-clients-cmg-azure)  

    - [Konfigurowanie odnajdywania użytkownika usługi Azure AD](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

    - Obsługuje niektóre [scenariusze bramy zarządzania w chmurze](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#scenarios)  

-   **Łącznik OMS**: [Połączenie do usługi Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS). Synchronizowanie danych, takich jak kolekcje w celu analizy dzienników OMS.  

-   **Uaktualnij łącznik gotowości**: Nawiązać module analiz systemu Windows [gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics). Wyświetl dane zgodności z uaktualnieniem klienta.  

-   **Microsoft sklepu dla firm**: Połączyć się z [Microsoft sklepu dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business). Pobierz aplikacje ze sklepu dla organizacji, które można wdrożyć z programem Configuration Manager.  

### <a name="service-details"></a>Szczegóły usługi

W poniższej tabeli przedstawiono szczegółowe informacje o każdym z nich.  

- **Dzierżawcy**: Liczba wystąpień usługi, które można skonfigurować. Każde wystąpienie musi być różne dzierżawą platformy Azure.  

- **Chmury**: Wszystkie usługi obsługuje globalnych chmury Azure, ale nie wszystkich usług pomocy technicznej chmur prywatnych, takich jak chmury Azure instytucji rządowych Stanów Zjednoczonych.  

- **Aplikacja sieci Web**: Określa, czy usługa korzysta z aplikacji usługi Azure AD typu *aplikacji sieci Web / interfejs API*, nazywany również aplikacji server w programie Configuration Manager.  

- **Aplikacji natywnej**: Określa, czy usługa korzysta z aplikacji usługi Azure AD typu *natywnego*, nazywany również aplikację klienta w programie Configuration Manager.  

- **Akcje**: Określa, czy można importować lub utworzyć tych aplikacji w Kreatorze usług Azure Menedżera konfiguracji.  


|Usługi  |Dzierżawcy  |Chmury  |Aplikacja sieci Web  |Aplikacji natywnej  |Akcje  |
|---------|---------|---------|---------|---------|---------|
|Zarządzanie chmury za pomocą</br>Odnajdowanie użytkowników usługi Azure AD | Wiele | Public | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | Importuj, tworzenie |
|Łącznik OMS | jeden | Publiczne, prywatne | ![Obsługiwane](media/green_check.png) | ![Nieobsługiwane](media/Red_X.png) | Importuj |
|Gotowości do uaktualnienia | jeden | Public | ![Obsługiwane](media/green_check.png) | ![Nieobsługiwane](media/Red_X.png) | Importuj |
|Microsoft magazynu dla</br>Działalności biznesowej i Education | jeden | Public | ![Obsługiwane](media/green_check.png) | ![Nieobsługiwane](media/Red_X.png) | Importuj, tworzenie |


### <a name="about-azure-ad-apps"></a>Temat aplikacji Azure AD

Różne usługi platformy Azure wymagają odrębne konfiguracje, które należy w portalu Azure. Ponadto aplikacje dla każdej usługi można wymagają oddzielnego uprawnienia do zasobów platformy Azure.  

Można użyć tylko jednej aplikacji dla wielu usług. Istnieje tylko jeden obiekt do zarządzania w programie Configuration Manager i usługi Azure AD. Po wygaśnięciu klucz zabezpieczeń w aplikacji, wystarczy Odśwież jeden klucz.

Najbezpieczniejszą konfigurację jest przy użyciu osobnych aplikacji dla każdej usługi. Aplikacja dla jednej usługi może wymagać dodatkowych uprawnień, które nie wymaga innej usługi. Zapewniają w aplikacji przy użyciu więcej uprawnień niż w przeciwnym razie wymaga dla różnych usług za pomocą jednej aplikacji. 

Po utworzeniu dodatkowych usług platformy Azure w Kreatorze programu Configuration Manager jest przeznaczona do ponownego użycia informacje, które są wspólne usługi. To zachowanie pomaga z konieczności wprowadzania tych samych informacji wiele razy. 

Aby uzyskać więcej informacji o uprawnieniach wymaganych aplikacji i konfiguracje dla poszczególnych usług, artykuł w odpowiednich programu Configuration Manager w [dostępnych usług](#available-services). 

Aby uzyskać więcej informacji na temat aplikacji Azure należy uruchomić z następujących artykułów:
- [Uwierzytelnianie i autoryzację w usłudze Azure App Service](/azure/app-service/app-service-authentication-overview)
- [Przegląd usługi Web Apps](/azure/app-service-web/app-service-web-overview)
- [Podstawowe informacje dotyczące rejestrowania aplikacji w usłudze Azure AD](/azure/active-directory/develop/active-directory-authentication-scenarios#basics-of-registering-an-application-in-azure-ad)  
- [Zarejestrować aplikację z dzierżawą usługi Azure Active Directory](/azure/active-directory/active-directory-app-registration)



## <a name="before-you-begin"></a>Przed rozpoczęciem

Po wybraniu usługi, z którym chcesz się połączyć, zgodnie z tabelą w [szczegóły dotyczące usługi](#service-details). Ta tabela zawiera informacje potrzebne do ukończenia Kreatora usługi Azure. Zostały omówione z wyprzedzeniem administrator usługi Azure AD. Zdecyduj, czy ręcznie tworzyć aplikacje wcześniej w portalu Azure, a następnie zaimportuj szczegóły aplikacji do programu Configuration Manager. Lub bezpośrednio utworzyć aplikacje w usłudze Azure AD za pomocą programu Configuration Manager. Aby zebrać niezbędne dane z usługi Azure AD, przejrzyj informacje w innych częściach niniejszego artykułu.

Niektóre usługi wymagają aplikacji Azure AD ma określone uprawnienia. Przejrzyj informacje dotyczące każdej usługi, aby określić wszystkie wymagane uprawnienia. Na przykład, aby można było zaimportować aplikację sieci web, administratora platformy Azure najpierw utworzyć ją w [portalu Azure](https://portal.azure.com). Podczas konfigurowania gotowości do uaktualnienia lub łącznika OMS, należy zapewnić aplikacji sieci web nowo zarejestrowanych *współautora* uprawnienia dla grupy zasobów, zawierającą odpowiedni obszar roboczy OMS. To uprawnienie umożliwia dostęp do tego obszaru roboczego program Configuration Manager. Wyszukaj nazwę rejestracji aplikacji w **dodawania użytkowników** bloku podczas przypisywania uprawnień. Ten proces jest taka sama jak kiedy [zapewnianie programu Configuration Manager z uprawnieniami do OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms). Administrator usługi Azure przypisać te uprawnienia przed zaimportowaniem aplikacji do programu Configuration Manager.



## <a name="start-the-azure-services-wizard"></a>Uruchom kreatora usług Azure

1.  W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **usługi w chmurze**i wybierz **usług Azure** węzła.  

2.  Na **Home** karty wstążki w **usług Azure** kliknij przycisk **Konfigurowanie usług Azure**.  

3.  Na **usług Azure** strony kreatora usług Azure:  

    1. Określ **nazwa** dla obiekt w programie Configuration Manager.  

    2. Określ opcjonalny **opis** pomoże zidentyfikować usługę.  

    3. Wybierz usługę Azure, którą chcesz się połączyć z programem Configuration Manager.  

4. Kliknij przycisk **dalej** w dalszym ciągu [właściwości aplikacji Azure](#azure-app-properties) strony kreatora usług Azure.  



## <a name="azure-app-properties"></a>Właściwości aplikacji Azure

Na **aplikacji** strony kreatora usług Azure, najpierw wybierz **środowiska platformy Azure** z listy. Odwołuje się do tabeli w [szczegóły dotyczące usługi](#service-details) dla środowiska, które jest obecnie dostępny dla usługi.

Pozostała część strony aplikacji zależy od określonej usługi. Odwołuje się do tabeli w [szczegóły dotyczące usługi](#service-details) usługa korzysta z typu aplikacji i jaka akcja można użyć. 
- Jeśli aplikacja obsługuje importu i tworzy akcje, kliknij przycisk **Przeglądaj**. Ta akcja powoduje otwarcie [serwera aplikacji w oknie dialogowym](#server-app-dialog) lub [aplikację klienta dla okna dialogowego](#client-app-dialog).
- Jeśli aplikacja obsługuje tylko akcję importu, kliknij przycisk **zaimportować**. Ta akcja powoduje otwarcie [okno dialogowe importowania aplikacji (serwer)](#import-apps-dialog-server) lub [okno dialogowe importowania aplikacji (klienta)](#import-apps-dialog-client).

Po określeniu aplikacje na tej stronie, kliknij przycisk **dalej** w dalszym ciągu [konfiguracji lub odnajdywania](#configuration-or-discovery) strony kreatora usług Azure.

### <a name="web-app"></a>Aplikacja sieci Web

Ta aplikacja jest typ usługi Azure AD *aplikacji sieci Web / interfejs API*, nazywany również aplikacji server w programie Configuration Manager.

#### <a name="server-app-dialog"></a>Okno dialogowe aplikacji serwera

Po kliknięciu **Przeglądaj** dla **aplikacji sieci Web** na stronie aplikacji Kreatora usług Azure go otwiera okno dialogowe aplikacji serwera. Wyświetla listę, która zawiera następujące właściwości wszystkich istniejących aplikacji sieci web:
- Przyjazna nazwa dzierżawy
- Przyjazna nazwa aplikacji
- Typ usługi

Istnieją trzy czynności, które można wykonać z okna dialogowego aplikacji serwera:
- Aby ponownie użyć istniejącej aplikacji sieci web, wybierz je z listy. 
- Kliknij przycisk **importu** otworzyć [importu aplikacji w oknie dialogowym](#import-apps-dialog-server).
- Kliknij przycisk **Utwórz** otworzyć [okna dialogowego Utwórz aplikację serwera](#create-server-application-dialog).

Po zaznaczeniu, zaimportować lub utworzenia aplikacji sieci web, kliknij przycisk **OK** aby zamknąć okno dialogowe aplikacji serwera. Ta akcja zwraca do [strony aplikacji](#azure-app-properties) kreatora usług Azure.

#### <a name="import-apps-dialog-server"></a>Importuj aplikacje okna dialogowego (serwer)

Po kliknięciu **importu** z okna dialogowego serwera aplikacji lub strony aplikacji w Kreatorze usług Azure go otwiera okno dialogowe aplikacji importu. Ta strona umożliwia wprowadzenie informacji o aplikacji sieci web usługi Azure AD, która jest już utworzone w portalu Azure. Importuje metadane dotyczące tej aplikacji sieci web do programu Configuration Manager. Podaj następujące informacje:
- **Nazwa dzierżawy usługi Azure AD**
- **Identyfikator dzierżawy usługi Azure AD**
- **Nazwa aplikacji**: Przyjazna nazwa aplikacji.
- **Identyfikator klienta**
- **Klucz tajny**
- **Wygaśnięcia klucza tajnego**: Wybierz przyszłą datę z kalendarza. 
- **Identyfikator URI aplikacji**: Ta wartość musi być unikatowa w dzierżawie usługi Azure AD. Jest używany przez klienta programu Configuration Manager, aby zażądać dostępu do usługi tokenu dostępu. Domyślnie ta wartość jest https://ConfigMgrService.  

Po wprowadzeniu informacji, kliknij przycisk **Sprawdź**. Następnie kliknij przycisk **OK** aby zamknąć okno dialogowe importowania aplikacji. Ta akcja zwraca jako [strony aplikacji](#azure-app-properties) kreatora usług Azure lub [serwera aplikacji w oknie dialogowym](#server-app-dialog).

#### <a name="create-server-application-dialog"></a>Tworzenie aplikacji serwera, okno dialogowe

Po kliknięciu **Utwórz** z okna dialogowego aplikacji serwera, otwiera okno dialogowe Tworzenie aplikacji serwera. Ta strona umożliwia zautomatyzowanie tworzenie aplikacji sieci web w usłudze Azure AD. Podaj następujące informacje:
- **Nazwa aplikacji**: Przyjazna nazwa aplikacji.
- **Adres URL strony głównej**: Ta wartość nie jest używany przez program Configuration Manager, ale wymagane przez usługę Azure AD. Domyślnie ta wartość jest https://ConfigMgrService.  
- **Identyfikator URI aplikacji**: Ta wartość musi być unikatowa w dzierżawie usługi Azure AD. Jest używany przez klienta programu Configuration Manager, aby zażądać dostępu do usługi tokenu dostępu. Domyślnie ta wartość jest https://ConfigMgrService.  
- **Okres ważności klucza tajnego**: kliknij przycisk listy rozwijanej i wybierz opcję **1 rok** lub **2 lata**. Rok jest wartością domyślną.

Kliknij przycisk **Zaloguj** uwierzytelnianie na platformie Azure jako użytkownik z uprawnieniami administracyjnymi. Te poświadczenia nie są zapisywane przez program Configuration Manager. Ta osoba nie wymaga uprawnień w programie Configuration Manager i nie musi być to samo konto, na którym uruchamiasz kreatora usług Azure. Po pomyślnym uwierzytelnieniu Azure na stronie znajdują się **nazwa dzierżawy Azure AD** odwołania. 

Kliknij przycisk **OK** do tworzenia aplikacji sieci web w usłudze Azure AD i zamknąć okno dialogowe Tworzenie aplikacji serwera. Ta akcja zwraca do [serwera aplikacji w oknie dialogowym](#server-app-dialog).


### <a name="native-client-app"></a>Aplikacja Native Client
    
Ta aplikacja jest typ usługi Azure AD *natywnego*, nazywany również aplikację klienta w programie Configuration Manager.

#### <a name="client-app-dialog"></a>Okno dialogowe aplikacji klienta

Po kliknięciu **Przeglądaj** dla **aplikacja Native Client** na stronie aplikacji Kreatora usług Azure go otwiera okno dialogowe aplikacji klienckiej. Wyświetla listę, która zawiera następujące właściwości wszelkie istniejące aplikacje natywne:
- Przyjazna nazwa dzierżawy
- Przyjazna nazwa aplikacji
- Typ usługi

Istnieją trzy czynności, które można wykonać z okna dialogowego aplikację klienta:
- Do ponownego użycia istniejącej aplikacji natywnej, wybierz go z listy. 
- Kliknij przycisk **importu** otworzyć [importu aplikacji w oknie dialogowym](#import-apps-dialog-client).
- Kliknij przycisk **Utwórz** otworzyć [okno dialogowe Tworzenie aplikacji klienckich](#create-client-application-dialog).

Po zaznaczeniu, zaimportować lub tworzenie natywnych aplikacji, kliknij przycisk **OK** aby zamknąć okno dialogowe aplikacji klienckiej. Ta akcja zwraca do [strony aplikacji](#azure-app-properties) kreatora usług Azure.

#### <a name="import-apps-dialog-client"></a>Importuj aplikacje okna dialogowego (klient)

Po kliknięciu **importu** w oknie dialogowym aplikacji klienckiej go otwiera okno dialogowe aplikacji importu. Ta strona umożliwia wprowadzenie informacji na temat usługi Azure AD natywnych aplikacji, która jest już utworzone w portalu Azure. Importuje metadane dotyczące tej aplikacji natywnej do programu Configuration Manager. Podaj następujące informacje:
- **Nazwa aplikacji**: Przyjazna nazwa aplikacji.
- **Identyfikator klienta** 

Po wprowadzeniu informacji, kliknij przycisk **Sprawdź**. Następnie kliknij przycisk **OK** aby zamknąć okno dialogowe importowania aplikacji. Ta akcja zwraca do [aplikację klienta dla okna dialogowego](#client-app-dialog).

#### <a name="create-client-application-dialog"></a>Tworzenie okna dialogowego aplikacji klienta

Po kliknięciu **Utwórz** w oknie dialogowym aplikacji klienckiej go otwiera okno dialogowe Tworzenie aplikacji klienckich. Ta strona umożliwia zautomatyzowanie tworzenie natywnych aplikacji w usłudze Azure AD. Podaj następujące informacje:
- **Nazwa aplikacji**: Przyjazna nazwa aplikacji.
- **Adres URL odpowiedzi**: Ta wartość nie jest używany przez program Configuration Manager, ale wymagane przez usługę Azure AD. Domyślnie ta wartość jest https://ConfigMgrService. 

Kliknij przycisk **Zaloguj** uwierzytelnianie na platformie Azure jako użytkownik z uprawnieniami administracyjnymi. Te poświadczenia nie są zapisywane przez program Configuration Manager. Ta osoba nie wymaga uprawnień w programie Configuration Manager i nie musi być to samo konto, na którym uruchamiasz kreatora usług Azure. Po pomyślnym uwierzytelnieniu Azure na stronie znajdują się **nazwa dzierżawy Azure AD** odwołania. 

Kliknij przycisk **OK** tworzenie natywnych aplikacji w usłudze Azure AD i zamknąć okno dialogowe Tworzenie aplikacji klienckich. Ta akcja zwraca do [aplikację klienta dla okna dialogowego](#client-app-dialog).


## <a name="configuration-or-discovery"></a>Konfiguracja lub odnajdywania

Po określeniu natywnych aplikacji sieci web i na stronie aplikacji, Kreator usług Azure przechodzi do albo **konfiguracji** lub **odnajdywania** strony, w zależności od usługi, z którym chcesz się połączyć. Szczegóły tej strony różnią się od usługi. Aby uzyskać więcej informacji zobacz następujące artykuły:  

-   **Chmury zarządzania** usługi, **odnajdywania** strony: [Konfigurowanie odnajdywania użytkownika usługi Azure AD](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

-   **Łącznik OMS** usługi, **konfiguracji** strony: [Skonfiguruj połączenie z usługą OMS](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#use-the-azure-services-wizard-to-configure-the-connection-to-oms)  

-   **Uaktualnij łącznik gotowości** usługi, **konfiguracji** strony: [Kreator Azure do utworzenia połączenia](/sccm/core/clients/manage/upgrade/upgrade-analytics#use-the-azure-wizard-to-create-the-connection)  

-   **Microsoft Store dla firm** usługi, **konfiguracje** strony: [Konfigurowanie Microsoft Store dla firm synchronizacji](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#for-configuration-manager-version-1706-and-later)  


Na koniec Ukończ Kreatora usług Azure na stronach podsumowania, postępie i zakończeniu. Konfigurowanie usługi Azure w programie Configuration Manager została ukończona. Powtórz ten proces, aby skonfigurować innymi usługami Azure.


## <a name="view-the-configuration-of-an-azure-service"></a>Widok konfiguracji usługi platformy Azure
Można wyświetlić właściwości usługi Azure, które zostały skonfigurowane do użycia. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **usługi w chmurze**i wybierz **usług Azure**. Wybierz usługę, aby wyświetlić lub edytować, a następnie kliknij przycisk **właściwości**.

Jeśli wybierz usługę, a następnie kliknij przycisk **usunąć** na Wstążce, ta akcja spowoduje usunięcie połączenia w programie Configuration Manager. Nie usuwa aplikacji w usłudze Azure AD. Poproś administratora platformy Azure, aby usunąć aplikację, gdy nie jest już potrzebne. Lub uruchom Kreatora usługi Azure, aby zaimportować aplikację.<!--483440-->


## <a name="cloud-management-data-flow"></a>Przepływ danych zarządzania w chmurze

Poniższy diagram jest przepływ danych koncepcyjnej interakcję między programem Configuration Manager, usługi Azure AD i połączone usługi w chmurze. W tym przykładzie określonych używane **zarządzania chmurą** usługi, która obejmuje klienta systemu Windows 10 oraz serwera i klienta aplikacji. Przepływy dla innych usług są podobne.

![Diagram przepływu danych programu Configuration Manager z usługą Azure AD i zarządzania w chmurze](media/aad-auth.png)

1.  Administrator programu Configuration Manager importuje lub tworzy klienta i serwera aplikacji w usłudze Azure AD.  

2.  Metoda odnajdywania użytkownika programu Configuration Manager Azure AD jest uruchamiany. Witryna używa tokenu aplikacji serwera usługi Azure AD w zapytaniu programu Microsoft Graph obiektów użytkownika.  

3.  Witryny przechowuje dane o obiektach użytkownika. Aby uzyskać więcej informacji, zobacz [odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).  

4.  Klient programu Configuration Manager żądania tokenu użytkownika usługi Azure AD. Klient wysyła oświadczeń przy użyciu Identyfikatora aplikacji i aplikacji serwera aplikacji klienta usługi Azure AD jako odbiorców. Aby uzyskać więcej informacji, zobacz [oświadczenia w tokenach zabezpieczających w usłudze Azure AD](/azure/active-directory/develop/active-directory-authentication-scenarios#claims-in-azure-ad-security-tokens).  

5.  Klient jest uwierzytelniany w witrynie z uwzględnieniem tokenu usługi Azure AD z bramą zarządzania w chmurze i/lub lokalnego punktu zarządzania z włączonym protokołem HTTPS.  


