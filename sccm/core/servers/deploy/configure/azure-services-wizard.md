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
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: e45d489a73d37f1bb174390ef48f939c5e081db0
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="configure-azure-services-for-use-with-configuration-manager"></a>Konfigurowanie usług platformy Azure do użytku z programem Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji Current Branch 1706, **Kreator usług Azure** jest używany w celu uproszczenia procesu konfigurowania usług Azure, możesz korzystać z programu Configuration Manager.

Ten kreator zapewnia typowych konfiguracji za pomocą **rejestracji aplikacji sieci web usługi Azure AD** Podaj szczegóły subskrypcji i konfiguracji do uwierzytelniania komunikacji z usługą Azure AD. Aplikacja sieci web zastępuje wprowadzania tych informacji każdorazowo, że zostało skonfigurowane do nowego składnika programu Configuration Manager lub usługi platformy Azure.

Następujących usług platformy Azure można skonfigurować za pomocą kreatora usług Azure:
-   **Zarządzanie chmury**   
    [Włącz klientów z uwierzytelniania za pomocą usługi Azure Active Directory](/sccm/core/clients/deploy/deploy-clients-cmg-azure) (Azure AD). Możesz również [skonfigurować odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc).
-   **Łącznik OMS**
    [Połącz z pakietem Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS) i synchronizowanie danych, takich jak kolekcje w celu analizy dzienników OMS.
-   **Gotowość do uaktualnienia**
    [nawiązywanie gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics) i przeglądać dane zgodności uaktualnienia klienta.
-   **Microsoft Store dla firm** nawiązać [Microsoft Store dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) i pobierania aplikacji dla organizacji, które można wdrożyć z programem Configuration Manager.

Konfigurowanie usługi za pomocą kreatora kilka typowych akcji są dostępne.
Należą do nich następujące elementy:
-   *Konfigurowanie środowiska Azure*:  Na **aplikacji** strony kreatora wybierz pozycję **środowiska platformy Azure** używanej. Zapoznaj się z materiałami dla każdej usługi dowiedzieć się, czy obsługuje tylko publiczne chmury Azure, czy obsługuje ona chmury prywatnej.
-   *Tworzenie lub importowanie aplikacji server*:   Na **aplikacji** strony kreatora, możesz **Utwórz** i **importu** metadanych rejestracji aplikacji sieci web platformy Azure. Dostępne opcje zależą od usługi konfiguracji. Ponadto niektóre usługi może wymagać dodatkowych aplikacji. Na przykład **chmury zarządzania** usługa wymaga **aplikacja Native Client** używany przez klientów do bezpośrednio uwierzytelniania komunikacji z usługami Azure.


Aby uzyskać informacje o aplikacjach sieci web platformy Azure, zobacz [uwierzytelnianie i autoryzację w usłudze Azure App Service](/azure/app-service/app-service-authentication-overview), i [Omówienie aplikacji sieci Web](/azure/app-service-web/app-service-web-overview).


## <a name="webapp"></a>Utwórz lub zaimportuj rejestracji aplikacji sieci web usługi Azure Active Directory do użycia z programem Configuration Manager

Rejestracji aplikacji sieci web usług Azure łączy z tej lokacji programu Configuration Manager do usługi Azure AD i jest wymaganiem wstępnym korzystania z infrastruktury przy użyciu usług Azure. Wykonaj następujące czynności:

1.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**, a następnie kliknij przycisk **usług Azure**.
2.  Na **Home** karcie **usług Azure** kliknij przycisk **Konfigurowanie usług Azure**.
3.  Na **usług Azure** strony kreatora usług Azure, wybierz usługę Azure, którą chcesz się połączyć z menedżerem konfiguracji.
4.  Na **ogólne** strona kreatora określ nazwę i opis usługi Azure.
5.  Na **aplikacji** strony kreatora wybierz środowisku platformy Azure z listy, a następnie kliknij przycisk **Przeglądaj** wybierz *aplikacji sieci Web* i *aplikacja Native Client* (tylko w razie potrzeby) który będzie używany do konfigurowania usługi Azure.

    **Aplikacja sieci Web:**   Przeglądaj powoduje otwarcie okna aplikacji serwera.    
      W **aplikacji Server** okna, aplikacji serwera, którego chcesz użyć, a następnie kliknij przycisk **OK**. Aplikacje serwera są rejestracji aplikacji sieci web usługi Azure AD, które zawierają konfiguracje dla konta platformy Azure, w tym Identyfikatora dzierżawy, identyfikator klienta i klucz tajny dla klientów.
    Jeśli nie ma dostępnych aplikacji, użyj jednej z następujących czynności:

    - **Utwórz**: Zautomatyzować tworzenie aplikacji sieci web rejestracji usługi Azure AD w oparciu o informacje, które możesz wpisać w konsoli programu Configuration Manager. Podaj przyjazną nazwę dla aplikacji, adres URL strony głównej, identyfikator URI aplikacji i okresu ważności klucza tajnego. Domyślnie okres ważności klucza tajnego jest jeden rok.
        
        Aby kontynuować, ktoś musi teraz zalogować się przy użyciu swoich poświadczeń usługi Azure AD, aby zakończyć tworzenie aplikacji sieci web na platformie Azure. Konto, którego używasz do logowania do usługi Azure nie musi być to samo konto, na którym uruchamiasz kreatora usług Azure. Po zalogowaniu się do platformy Azure, programu Configuration Manager utworzy aplikację sieci web na platformie Azure, w tym identyfikator klienta i klucz tajny do użycia z aplikacji sieci web. Później możesz wyświetlić te z portalu Azure.

        Jeśli używasz *Utwórz* do skonfigurowania aplikacji sieci web, programu Configuration Manager może utworzyć aplikacji sieci web dla Ciebie w usłudze Azure AD.
    
    - **Importuj**: Wprowadź informacje o rejestracji aplikacji sieci web usługi Azure AD, który został już utworzony w **portalu Azure** Aby zaimportować metadane dotyczące tej rejestracji do programu Configuration Manager. Podaj przyjazną nazwę dla aplikacji i dzierżawy, a następnie określ identyfikator dzierżawy, identyfikator klienta i klucz tajny aplikacji sieci web platformy Azure, który program Configuration Manager do użycia. Po sprawdzeniu informacji, kliknij przycisk **OK** aby kontynuować.
        > [!NOTE]
        > Przed **importu** mogą być używane, rejestracji aplikacji usługi Azure AD typu *aplikacji sieci Web / interfejs API* muszą być tworzone w [portalu Azure](https://portal.azure.com). Aby przeczytać więcej informacji na temat sposobu tworzenia rejestracji aplikacji, zobacz [zarejestrować aplikację z dzierżawą usługi Azure Active Directory](/azure/active-directory/active-directory-app-registration). Podczas konfigurowania gotowości do uaktualnienia lub Operations Management Suite, należy również udzielenia aplikacji sieci web nowo zarejestrowanych *współautora* uprawnienia dla grupy zasobów, zawierającą odpowiedni obszar roboczy OMS Aby Configuration Manager, aby można było uzyskać dostępu do tego obszaru roboczego. Aby to zrobić, należy wyszukać nazwę rejestracji aplikacji w **dodawania użytkowników** bloku podczas przypisywania uprawnień. Jest to ten sam proces, który musi znajdować się po podczas [zapewnianie programu Configuration Manager z uprawnieniami do OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) dla połączeń z [analizy dzienników](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm). Przed aplikacji jest importowany do programu Configuration Manager, należy przypisać te uprawnienia.


    **Aplikacja Native Client:**  Przeglądaj powoduje otwarcie okna aplikacji klienckiej.  
     W **aplikacji klienckiej** okna, aplikację klienta, którego chcesz użyć, a następnie kliknij przycisk **OK**.

     Jeśli nie ma dostępnych klienta aplikacji, użyj jednej z następujących czynności:
     - **Utwórz**: Aby utworzyć nową aplikację klienta, kliknij przycisk **Utwórz**. Następnie Podaj przyjazną nazwę i identyfikator URI przekierowania aplikacji.

         Aby kontynuować, ktoś musi teraz Zaloguj się przy użyciu poświadczeń usługi Azure AD, aby zakończyć tworzenie aplikacji sieci web na platformie Azure. Konto, którego używasz do logowania do platformy Azure nie musi być to samo konto, na którym uruchamiasz kreatora usług Azure. Po zalogowaniu do platformy Azure programu Configuration Manager utworzy aplikację klienta natywnego w usłudze Azure AD, takie jak identyfikator klienta i klucz tajny. Później, można wyświetlić je z [portalu Azure](https://portal.azure.com). 

     - **Importuj**: Użyj aplikacji klienckiej, która już istnieje w subskrypcji platformy Azure. Podaj przyjazną nazwę dla aplikacji i identyfikatorem klienta. Następnie kliknij przycisk **OK** aby kontynuować.

  <!--  MOVE THIS AND STEP 6 TO configure Azure AD User Discover  content
       [!TIP]  
     When you use Import, the account you use to run the wizard must have the *Read directory data* application permission in the Azure portal. This is required to set the correct permissions for the App. When you use Create, Configuration Manager creates the app with the correct permissions. However, you still must give consent to the application in the Azure portal.   -->


6.  (Tylko podczas konfigurowania **zarządzania w chmurze** usługi) w **odnajdywania** strony kreatora, kliknij przycisk **włączyć Azure użytkownika odnajdywania usługi Active Directory**, a następnie kliknij przycisk  **Ustawienia**.
W **ustawienia odnajdywania usługi Azure AD użytkownika** okna dialogowego Skonfiguruj harmonogram po wystąpieniu odnajdywania. Można również włączyć odnajdowania różnicowego, który sprawdza, czy tylko nowe lub zmienione kont w usłudze Azure AD. Dowiedz się więcej o [odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

7.  Ukończ pracę kreatora.

W tym momencie ukończono konfigurację usługi Azure w programie Configuration Manager. Może Powtórz ten proces, aby skonfigurować innymi usługami Azure.

## <a name="view-the-configuration-of-an-azure-service"></a>Widok konfiguracji usługi platformy Azure
Można wyświetlić właściwości usługi Azure, które zostały skonfigurowane do użycia.

W konsoli przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **usług Azure**. Następnie wybierz usługę, aby wyświetlić lub edytować, a następnie kliknij przycisk **właściwości**.
