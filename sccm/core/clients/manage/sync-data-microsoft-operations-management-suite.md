---
title: "Synchronizowanie danych | Dokumenty Microsoft | Pakiet zarządzania Operations firmy Microsoft "
description: "Synchronizowanie danych z programu System Center Configuration Manager do pakietu zarządzania Operations firmy Microsoft."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 33bcf8b3-a6b6-4fc9-bb59-70a9621b2b0d
caps.latest.revision: 9
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3acfaa2cf8c64ece5cef65b80372067336d6a815
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---


# <a name="sync-data-from-configuration-manager-to-the-microsoft-operations-management-suite"></a>Zsynchronizuj dane z programu Configuration Manager do pakietu zarządzania Operations firmy Microsoft


*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przykład kolekcji z programu System Center Configuration Manager do analizy dziennika usługi OMS platformy Microsoft Azure, można użyć łącznika usługi Microsoft Operations Management Suite (OMS) w celu synchronizacji danych. Dzięki temu danych z wdrożenia programu Configuration Manager są widoczne w usługi OMS.
> [!TIP]
> Łącznik usługi OMS jest funkcją wersji wstępnej. Aby dowiedzieć się więcej, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/pre-release-features).

Począwszy od wersji 1702, można używać łącznika usługi OMS się połączyć z obszarem roboczym usługi OMS znajdującego się w chmurze Microsoft Azure Rząd. Należy zmodyfikować plik konfiguracji, należy zainstalować łącznik usługi OMS. Zobacz [korzystania z łącznika usługi OMS z chmury Azure rządu](#fairfaxconfig) w tym temacie.

## <a name="prerequisites"></a>Wymagania wstępne
- Przed zainstalowaniem łącznika usługi OMS w programie Configuration Manager, należy podać programu Configuration Manager z uprawnieniami do usługi OMS. W szczególności należy przyznać *dostępu współautora* Azure *grupy zasobów* zawierający obszar roboczy usługi OMS dziennika analizy. Procedury przedstawione w tym celu są udokumentowane w zawartość dziennika analizy. Zobacz [zapewniają programu Configuration Manager z uprawnieniami do usługi OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms) w dokumentacji usługi OMS.

- Łącznik usługi OMS musi być zainstalowany na komputerze, który obsługuje [punktem połączenia usługi](/sccm/core/servers/deploy/configure/about-the-service-connection-point) w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#a-namebkmkmodesa-modes-of-operation).

  Jeśli nawiązano połączenie usługi OMS do autonomicznej lokacji głównej i planowane jest dodanie witryny Administracja centralna w danym środowisku, musi usunąć bieżące połączenie, a następnie skonfigurować łącznik z nową witryną Administracja centralna.

- Dla usługi OMS zainstalowane na punkt połączenia usługi wraz z łącznika usługi OMS, należy zainstalować program Microsoft Monitoring Agent.  Agent i łącznika usługi OMS muszą być skonfigurowane do używania takie same **obszaru roboczego usługi OMS**. Aby zainstalować agenta, zobacz [pobrać i zainstalować agenta](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#download-and-install-the-agent) w dokumentacji usługi OMS.

- Po zainstalowaniu łącznika i agenta, należy skonfigurować usługi OMS używanie danych programu Configuration Manager.  Aby to zrobić, w portalu usługi OMS możesz [kolekcji programu Configuration Manager importu](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#import-collections).



## <a name="install-the-oms-connector"></a>Zainstalować łącznik usługi OMS  
1. W konsoli programu Configuration Manager, należy skonfigurować Twoje [hierarchii w celu korzystania z funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features), a następnie Włącz użycie łącznika usługi OMS.  

2. Następnie należy przejść do **Administracja** > **usług w chmurze** > **łącznika usługi OMS**. Na wstążce kliknij przycisk "Utwórz połączenia na pakiet zarządzania Operations". Spowoduje to otwarcie **połączenie kreatora pakiet zarządzania operacji**. Wybierz **dalej**.  


3.    Na **ogólne** strony, sprawdź, czy następujące informacje, a następnie wybierz **dalej**.  
  - Zarejestrowany programu Configuration Manager, jak narzędzia do zarządzania "API sieci Web i/lub aplikacji sieci Web", a [Identyfikatora klienta z tej rejestracji](https://docs.microsoft.com/azure/active-directory/develop/active-directory-integrating-applications).  
  - Utworzono klucz klienta dla narzędzia do zarządzania zarejestrowanych w usłudze Azure Active Directory.  

  - W portalu zarządzania Azure podany aplikacji sieci web zarejestrowanych uprawnień dostępu do usługi OMS, zgodnie z opisem w [zapewniają programu Configuration Manager z uprawnieniami do usługi OMS](https://docs.microsoft.com/azure/log-analytics/log-analytics-sccm#provide-configuration-manager-with-permissions-to-oms).  

4.    Na **Azure Active Directory** Skonfiguruj ustawienia połączenia usługi OMS podając swoje **dzierżawy**, **Identyfikatora klienta**, i **klucz tajny klienta**, a następnie zaznacz pozycję **dalej**.  

5.    Na **konfiguracji połączenia usługi OMS** Podaj ustawienia połączenia, wypełniając swoje **subskrypcji Azure**, **grupy zasobów Azure**, i **obszaru roboczego pakiet zarządzania Operations**.  Obszar roboczy musi odpowiadać obszar roboczy, który jest skonfigurowany dla agenta zarządzania firmy Microsoft zainstalowanego na punkt połączenia usługi.  

6.    Sprawdź ustawienia połączenia na **Podsumowanie** strony, a następnie wybierz **dalej**. **Postępu** strony wyświetlany jest stan połączenia należy następnie **zakończone**.

Po połączeniu programu Configuration Manager do usługi OMS, można dodać lub usunąć kolekcje i wyświetlić właściwości połączenia usługi OMS.

## <a name="verify-the-oms-connector-properties"></a>Sprawdź właściwości łącznika usługi OMS
1.    W konsoli programu Configuration Manager, przejdź do **Administracja** > **usług w chmurze**, a następnie wybierz **łącznika usługi OMS** otworzyć **połączenia usługi OMS ** strony**.
2.    Na tej stronie istnieją dwie karty:
  - **Azure Active Directory:**   
    Ta karta przedstawia swoje **dzierżawy**, **Identyfikatora klienta**, **wygaśnięcia klucza tajnego klienta**, i pozwala na zweryfikowanie klucz tajny klienta utracił ważność.

  - **Właściwości połączenia usługi OMS:**  
    Na tej karcie wyświetlane z **subskrypcji Azure**, **grupy zasobów Azure**, **obszaru roboczego pakiet zarządzania Operations**i listę **kolekcji urządzeń, które pakiet zarządzania Operations można uzyskać danych dla**. Użyj **Dodaj** i **Usuń** przycisków, aby zmodyfikować kolekcji, które są dozwolone.

## <a name="fairfaxconfig"></a> Korzystania z łącznika usługi OMS z chmurą Rząd Azure


1.  Na dowolnym komputerze z zainstalowaną konsolą programu Configuration Manager należy edytować następujący plik konfiguracji do punktu w chmurze rząd:  ***&lt;Ścieżka instalacji CM > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Zmiany:**

    Zmień wartość atrybutu Nazwa ustawienia *FairFaxArmResourceID* powinna być równa "https://management.usgovcloudapi.net/"

   - **Oryginalne:** 
      &lt;Nazwa ustawienia = "FairFaxArmResourceId" serializeAs = "String" >   
      &lt;wartość > &lt; /value >   
      &lt;/ Ustawienia >

   - **Edycji:**     
      &lt;Nazwa ustawienia = "FairFaxArmResourceId" serializeAs = "String" > &lt;wartość > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ Ustawienia >

  Zmień wartość atrybutu Nazwa ustawienia *FairFaxAuthorityResource* powinna być równa "https://login.microsoftonline.com/"

  - **Oryginalne:** &lt;Nazwa ustawienia = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > &lt; /value >

    - **Edytować:** &lt;ustawienie name = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > https://login.microsoftonline.com/ &lt; /value >

2.    Po zapisaniu pliku z dwie zmiany, ponownie uruchom konsolę programu Configuration Manager na tym samym komputerze, a następnie użyj konsoli instalacji łącznika usługi OMS. Aby zainstalować łącznik, informacje zawarte w [synchronizowanie danych z programu Configuration Manager do pakietu zarządzania Microsoft Operations](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)i wybierz **obszaru roboczego pakiet zarządzania Operations** znajdujący się w chmurze Microsoft Azure Rząd.

3.    Po zainstalowaniu łącznika usługi OMS połączenia w chmurze rząd jest dostępna, korzystając z każdej konsoli, który połączy się z lokacją.

