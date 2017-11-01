---
title: "Kreator usług Azure"
titleSuffix: Configuration Manager
description: "Kreator usług platformy Azure dla programu System Center Configuration Manager — informacje"
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: a26a653e-17aa-43eb-ab36-0e36c7d29f49
caps.latest.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 1e26c87d7f5edef3443496ac87c1edcf71271470
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Konfigurowanie usług platformy Azure do użytku z programem Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji Current Branch 1706, **Kreator usług Azure** jest używany w celu uproszczenia procesu konfigurowania usług platformy Azure, możesz korzystać z programu Configuration Manager.

Ten kreator zapewnia typowych konfiguracji za pomocą **aplikacji sieci web Azure** podać szczegóły subskrypcji i konfiguracji. Aplikacja sieci web zastępuje wprowadzania tych informacji każdorazowo, że zostało skonfigurowane do nowego składnika programu Configuration Manager lub usługi platformy Azure.

Następujących usług platformy Azure są konfigurowane za pomocą Kreatora konfigurowania usług Azure:
-   **Zarządzanie chmury**   
    [Włącz klientów z uwierzytelniania za pomocą usługi Azure Active Directory](/sccm/core/clients/deploy/deploy-clients-cmg-azure) (Azure AD). Możesz również [skonfigurować odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc).
-   **Łącznik OMS**
    [Połącz z programu Operations Manager Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS) i synchronizowanie danych, takich jak kolekcje w celu analizy dzienników OMS.
-   **Gotowość do uaktualnienia**
    [nawiązywanie gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) i przeglądać dane zgodności uaktualnienia klienta.
-   **Sklep Windows dla firm** nawiązywanie w sklepie online [Sklep Windows dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) i pobierania aplikacji dla organizacji, które można wdrożyć z programem Configuration Manager.

Konfigurowanie usługi za pomocą kreatora kilka typowych akcji są dostępne.
Należą do nich następujące elementy:
-   Konfigurowanie środowiska platformy Azure:  Na **aplikacji** strony kreatora należy wybrać **środowiska platformy Azure** używanej. Zapoznaj się z materiałami dla każdej usługi dowiedzieć się, czy obsługuje tylko publiczne chmury Azure, czy obsługuje ona chmury prywatnej.
-   Tworzenie lub importowanie aplikacji serwera:   Na **aplikacji** strony kreatora, możesz **Utwórz** i **importu** aplikacji sieci web platformy Azure. Dostępne opcje zależą od usługi, który jest konfigurowany.  Ponadto niektóre usługi może wymagać dodatkowych aplikacji. Na przykład usługa może być także wymagane **aplikacja Native Client**.


Aby uzyskać informacje o aplikacjach sieci web platformy Azure, zobacz [uwierzytelnianie i autoryzację w usłudze Azure App Service](/azure/app-service/app-service-authentication-overview), i [aplikacji sieci Web — Omówienie](/azure/app-service-web/app-service-web-overview)


## <a name="webapp"></a>Tworzenie aplikacji sieci web platformy Azure do użytku w programie Configuration Manager

Aplikacja sieci web usług Azure łączy z tej lokacji programu Configuration Manager z usługą Azure AD i jest wymaganiem wstępnym korzystania z infrastruktury przy użyciu usług Azure. Wykonaj następujące czynności:

1.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, a następnie kliknij przycisk **usług Azure**.
2.  Na **Home** karcie **usług Azure** kliknij przycisk **Konfigurowanie usług Azure**.
3.  Na **usług Azure** kreatora usług Azure, wybierz **zarządzania chmurą** do zezwalania klientom do uwierzytelniania za pomocą hierarchii przy użyciu usługi Azure AD.
4.  Na **ogólne** strona kreatora określ nazwę i opis usługi Azure.
5.  Na **aplikacji** strony kreatora wybierz środowisku platformy Azure z listy, a następnie kliknij przycisk **Przeglądaj** wybierz *aplikacji sieci Web* i *aplikacja Native Client* który będzie używany do konfigurowania usługi Azure.     
    **Aplikacja sieci Web:**   Przeglądaj powoduje otwarcie okna aplikacji serwera.    
      W **aplikacji Server** okna, aplikacji serwera, którego chcesz użyć, a następnie kliknij przycisk **OK**. Aplikacje serwera są aplikacjami sieci web platformy Azure, które zawierają konfiguracje dla konta platformy Azure, w tym Identyfikatora dzierżawy, identyfikator klienta i klucz tajny dla klientów.
    Jeśli nie ma dostępnych aplikacji, użyj jednej z następujących czynności:
        - **Utwórz**: Aby utworzyć nową aplikację serwera, kliknij przycisk **Utwórz**. Następnie Podaj przyjazną nazwę dla aplikacji, adres URL strony głównej, identyfikator URI aplikacji i okresu ważności klucza tajnego. Domyślnie okres ważności klucza tajnego jest jeden rok.

         Aby kontynuować, ktoś musi teraz logowania do platformy Azure, aby zakończyć tworzenie aplikacji sieci web na platformie Azure. Konto, którego używasz do logowania do platformy Azure nie musi być to samo konto, na którym uruchamiasz kreatora usług Azure. Po zalogowaniu do platformy Azure programu Configuration Manager utworzy aplikację sieci web na platformie Azure, w tym identyfikator klienta i klucz tajny do użycia z aplikacji sieci web. Później możesz wyświetlić te z portalu Azure.

         Podczas tworzenia są używane do konfigurowania aplikacji sieci web, programu Configuration Manager można utworzyć aplikacji sieci web dla Ciebie w usłudze Azure AD.
        - **Importuj**: Aby korzystać z aplikacji sieci web, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i dzierżawy, a następnie określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po sprawdzeniu informacji, kliknij przycisk **OK** aby kontynuować.

          Ta opcja nie jest dostępna dla wszystkich usług, które można skonfigurować.

   **Aplikacja Native Client:**  Przeglądaj powoduje otwarcie okna aplikacji klienckiej.  
     W **aplikacji klienckiej** okna, aplikację klienta, którego chcesz użyć, a następnie kliknij przycisk **OK**.

     Jeśli nie ma dostępnych klienta aplikacji, użyj jednej z następujących czynności:
     - **Utwórz**: Aby utworzyć nową aplikację klienta, kliknij przycisk **Utwórz**. Następnie Podaj przyjazną nazwę dla aplikacji i adres URL odpowiedzi.

          Aby kontynuować, ktoś musi teraz logowanie do platformy Azure aby zakończyć tworzenie aplikacji klienckich w usłudze Azure. Konto, którego używasz do logowania do platformy Azure nie musi być to samo konto, na którym uruchamiasz kreatora usług Azure. Po zalogowaniu do platformy Azure programu Configuration Manager utworzy aplikację klienta natywnego na platformie Azure, łącznie z Identyfikatorem klienta do użycia z aplikacji sieci web. Później możesz wyświetlić te z portalu Azure.
          Gdy używasz Utwórz do skonfigurowania aplikacji programu Configuration Manager można utworzy aplikację klienta natywnego w usłudze Azure AD.
     - **Importuj**: Aby korzystać z aplikacji klienckiej, która już istnieje w subskrypcji platformy Azure, kliknij przycisk **importu**. Podaj przyjazną nazwę dla aplikacji i identyfikatorem klienta. Następnie kliknij przycisk **OK** aby kontynuować.
           Ta opcja nie jest dostępna dla wszystkich usług, które można skonfigurować.

  <!--  MOVE THIS AND STEP 6 TO configure Azure AD User Discover  content
       [!TIP]  
     When you use Import, the account you use to run the wizard must have the *Read directory data* application permission in the Azure portal. This is required to set the correct permissions for the App. When you use Create, Configuration Manager creates the app with the correct permissions. However, you still must give consent to the application in the Azure portal.   -->


6.  Na **odnajdywania** strony kreatora, kliknij przycisk **włączyć Azure użytkownika odnajdywania usługi Active Directory**, a następnie kliknij przycisk **ustawienia**.
W **ustawienia odnajdywania usługi Azure AD użytkownika** okna dialogowego Skonfiguruj harmonogram po wystąpieniu odnajdywania. Można również włączyć odnajdowania różnicowego, który sprawdza, czy tylko nowe lub zmienione kont w usłudze Azure AD. Dowiedz się więcej o [odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

 7. Ukończ pracę kreatora.

W tym momencie połączyły tej lokacji programu Configuration Manager z usługą Azure AD.

## <a name="view-the-configuration-of-an-azure-service"></a>Widok konfiguracji usługi platformy Azure
Można wyświetlić właściwości usługi Azure, które zostały skonfigurowane do użycia.

W konsoli przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **usług Azure**. Następnie wybierz usługę, aby wyświetlić lub edytować, a następnie kliknij przycisk **właściwości**.
