---
title: Gotowości do uaktualnienia
titleSuffix: System Center Configuration Manager
description: Integracja z programem Configuration Manager gotowości do uaktualnienia. Dane zgodności z uaktualnieniem dostępu w konsoli administracyjnej. Urządzenia docelowe dla uaktualnienia lub korygowania.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-client
ms.assetid: 68407ab8-c205-44ed-9deb-ff5714451624
ms.openlocfilehash: f9fec1723c5242485d23981bcb683e3a8e98bfd3
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="integrate-upgrade-readiness-with-system-center-configuration-manager"></a>Integracja gotowości do uaktualnienia z programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Gotowości do uaktualnienia (dawniej uaktualnienia Analytics) jest częścią [module analiz systemu Windows](https://www.microsoft.com/WindowsForBusiness/windows-analytics) umożliwiająca do oceny i analizowania gotowości urządzeń w środowisku do uaktualnienia do systemu Windows 10. Można skonfigurować określonej wersji. Gotowości do uaktualnienia można zintegrować z programem Configuration Manager dostępu do danych zgodności z uaktualnieniem klienta w konsoli administracyjnej programu Configuration Manager. Można na urządzenia docelowe do uaktualnienia lub korygowania przy użyciu kolekcji dynamiczne utworzone na podstawie tego danych.

Gotowości do uaktualnienia to rozwiązanie, które działa na [Operations Management Suite (OMS)](/azure/operations-management-suite/operations-management-suite-overview). Więcej o uaktualnienie gotowości w [uaktualnia Zarządzanie systemem Windows z gotowości do uaktualnienia](/windows/deployment/upgrade/manage-windows-upgrades-with-upgrade-readiness).

>[!WARNING]
>Uaktualnij gotowości do funkcji w programie Configuration Manager musisz najpierw uaktualnić do 1802 wersji programu Configuration Manager.  <!--507205--> Łącznik gotowości uaktualnienia nie będą działać starszych niż 1802 w wersjach programu Configuration Manager. 


## <a name="configure-clients"></a>Konfigurowanie klientów

Gotowości do uaktualnienia, podobnie jak wszystkie rozwiązania w module analiz systemu Windows, zależy od danych telemetrycznych systemu Windows. Aby uaktualnić gotowości do odbierania wystarczającą ilość danych telemetrii muszą być spełnione następujące wymagania wstępne:

- Wszyscy klienci muszą mieć skonfigurowaną **komercyjnych klucza Identyfikatora**. 
- Klienci systemu Windows 10 muszą mieć telemetrii skonfigurowany tak, aby zgłosić co najmniej podstawowego poziomu danych telemetrycznych.
-  Klienci z wcześniejszymi wersjami w systemie Windows muszą mieć zainstalowany określonych KB/s zgodnie z opisem w [wprowadzenie gotowości do uaktualnienia](/windows/deployment/upgrade/upgrade-readiness-get-started#deploy-the-compatibility-update-and-related-kbs). Muszą mieć włączone w danych telemetrycznych **ustawień klienta**.

Komercyjnych klucza Identyfikatora i dane telemetryczne systemu Windows można skonfigurować w **ustawień klienta**. Aby dowiedzieć się więcej, zobacz [module analiz systemu Windows używana z programem Configuration Manager](../monitor-windows-analytics.md).

>[!NOTE]
>Jeśli wystąpią problemy z gotowości uaktualnienia nie odbiera danych telemetrycznych z urządzeń w danym środowisku, zgodnie z oczekiwaniami, a następnie niektórych z tych problemów może być kierowane za pomocą [skrypt wdrożenia uaktualnienia gotowości](/windows/deployment/upgrade/upgrade-readiness-deployment-script). Jednak w większości środowisk wdrażania poprawne KB/s, konfigurowanie komercyjnych klucza Identyfikatora i telemetrii w **ustawień klienta** powinno wystarczyć.

## <a name="connect-configuration-manager-to-upgrade-readiness"></a>Połącz gotowości do uaktualnienia program Configuration Manager

Począwszy od wersji Current Branch 1706, [Kreator usług Azure](../../../servers/deploy/configure/azure-services-wizard.md) jest używany w celu uproszczenia procesu konfigurowania usług platformy Azure, możesz korzystać z programu Configuration Manager. Do łączenia programu Configuration Manager z gotowości do uaktualnienia, rejestracji aplikacji usługi Azure AD typu *aplikacji sieci Web / interfejs API* muszą być tworzone w [portalu Azure](https://portal.azure.com). Aby przeczytać więcej informacji na temat sposobu tworzenia rejestracji aplikacji, zobacz [zarejestrować aplikację z dzierżawą usługi Azure Active Directory](/azure/active-directory/active-directory-app-registration). W **portalu Azure**, należy również podać aplikacji sieci web nowo zarejestrowanych *współautora* uprawnienia na grupę zasobów, która zawiera obszar roboczy OMS służącą do hostowania danych gotowości do uaktualnienia. **Kreator usług Azure** użyje tej rejestracji aplikacji można umożliwić programowi Configuration Manager do bezpiecznego komunikowania się z usługą Azure AD i Połącz z danymi gotowości do uaktualnienia infrastruktury.

>[!IMPORTANT]
>*Współautor* muszą mieć uprawnienia do aplikacji w przeciwieństwie do usługi Azure AD tożsamości użytkownika. Jest tak, ponieważ jest on zarejestrowany aplikacji i nie użytkownika usługi Azure AD, który uzyskuje dostęp do danych w imieniu infrastruktury programu Configuration Manager. Aby udzielić uprawnień, należy wyszukać nazwę rejestracji aplikacji w **dodawania użytkowników** obszaru podczas przypisywania uprawnień. Tego samego procesu, który musi występować po [zapewnianie programu Configuration Manager z uprawnieniami do OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) dla połączeń z [analizy dzienników](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm). Te kroki należy wykonać przed rejestracji aplikacji jest importowany do programu Configuration Manager z *Kreator usług Azure*.

### <a name="use-the-azure-wizard-to-create-the-connection"></a>Kreator Azure do utworzenia połączenia

Postępuj zgodnie z instrukcjami [usług Azure skonfigurować do użytku z programem Configuration Manager](../../../servers/deploy/configure/azure-services-wizard.md) utworzyć połączenie gotowości do uaktualnienia, importując rejestracji aplikacji sieci web utworzone powyżej. 

Na *konfiguracji* strony, są następujące wartości wstępnie wypełnione importowanie aplikacji sieci web zakończyło się pomyślnie, jeśli przypisano odpowiednie uprawnienia w **portalu Azure**. 
-  Subskrypcje platformy Azure
-  Grupy zasobów platformy Azure
-  Obszar roboczy w module analiz systemu Windows

Więcej niż jednej grupy zasobów lub obszar roboczy będzie tylko w przypadku aplikacji sieci web zarejestrowane usługi Azure AD ma *współautora* uprawnienia do więcej niż jednej grupy zasobów lub jeśli wybranej grupy zasobów ma więcej niż jeden obszar roboczy OMS.
 
## <a name="view-and-use-upgrade-readiness-information-in-configuration-manager"></a>Wyświetlanie i używanie informacji gotowości do uaktualnienia w programie Configuration Manager

Po gotowości do uaktualnienia został zintegrowany z programem Configuration Manager, można wyświetlić analizy gotowości do uaktualnienia klientów.

1. W konsoli programu Configuration Manager wybierz **monitorowanie** > **omówienie** > **gotowości do uaktualnienia**.
2. Przejrzyj dane, w tym stan gotowości do uaktualnienia i odsetek urządzeń z systemem Windows, które są raportowania danych telemetrycznych.
3. Można filtrować pulpit nawigacyjny, aby wyświetlić dane dla urządzenia w określonej kolekcji.
4. Możesz wyświetlić stan gotowości określonego urządzenia i tworzenie kolekcji dynamicznych dla tych urządzeń, tak, aby uaktualnić tych urządzeń, jeśli jest to gotowe lub podjąć działania w celu korygowania urządzeń z zablokowanym dostępem do uaktualnienia.

## <a name="using-the-upgrade-readiness-connector-version-1702-and-earlier"></a>Za pomocą łącznika gotowości uaktualnienia (wersja 1702 i starsze)

1702 wersji programu Configuration Manager lub wcześniej zestaw kroków i wymagania są niezbędne do utworzenia połączenia gotowości do uaktualnienia.

### <a name="prerequisites"></a>Wymagania wstępne

- Aby dodać połączenie, najpierw należy skonfigurować środowiska programu Configuration Manager [punkt połączenia z usługą](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](https://azure.microsoft.com/documentation/articles/resource-group-create-service-principal-portal/). Po dodaniu połączenia ze środowiskiem go spowoduje także zainstalowanie programu Microsoft Monitoring Agent na komputerze, na którym działa ta rola systemu lokacji.
- Zarejestruj programu Configuration Manager jako narzędzie do zarządzania "API sieci Web i/lub aplikacji sieci Web" oraz możliwość uzyskania [identyfikator klienta z tej rejestracji](https://azure.microsoft.com/documentation/articles/active-directory-integrating-applications/).
- Utwórz klucz klienta dla zarejestrowanego narzędzia do zarządzania w usłudze Azure Active Directory.
- W portalu Azure, podaj aplikacji sieci web w zarejestrowany z uprawnieniami do OMS, zgodnie z opisem w [Podaj programu Configuration Manager z uprawnieniami do OMS](https://azure.microsoft.com/documentation/articles/log-analytics-sccm/#provide-configuration-manager-with-permissions-to-oms).

    > [!IMPORTANT]
    > Podczas konfigurowania uprawnień dostępu OMS, należy wybrać **współautora** roli i przypisz mu uprawnienia do grupy zasobów w zarejestrowany aplikacji.

### <a name="create-the-connection"></a>Utwórz połączenie

1.  W konsoli programu Configuration Manager wybierz **administracji** > **usługi w chmurze** > **uaktualnienia łącznik gotowości** > **utworzyć połączenie uaktualnienia Analytics** można uruchomić **dodać uaktualnienia Kreator połączenia Analytics**.
3.  Na **usługi Azure Active Directory** ekranu, podaj **dzierżawy**, **identyfikator klienta**, i **klucza tajnego klienta**, a następnie wybierz pozycję **dalej**.
4.  Na **gotowości do uaktualnienia** ekranu, podać ustawienia połączenia, wypełniając Twojej **subskrypcji platformy Azure**, **grupy zasobów platformy Azure**, i **obszar roboczy usługi Operations Management Suite**.
5.  Sprawdź ustawienia połączenia w **Podsumowanie** ekranu, a następnie wybierz **dalej**.

    > [!NOTE]
    > Należy połączyć gotowości do uaktualnienia lokacji najwyższego poziomu w hierarchii. Jeśli możesz połączyć uaktualnienia gotowości do autonomicznej lokacji głównej, a następnie dodać centralną lokację administracyjną do środowiska, należy usunąć i Utwórz ponownie połączenie OMS w nowej hierarchii.
