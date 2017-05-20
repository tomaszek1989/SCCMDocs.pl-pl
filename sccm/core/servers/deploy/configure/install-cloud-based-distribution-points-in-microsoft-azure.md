---
title: Punkty dystrybucji w chmurze | Dokumentacja firmy Microsoft
description: "Dowiedz się, co należy zrobić, aby rozpocząć korzystanie z punktów dystrybucji w chmurze platformy Microsoft Azure."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f96905f50f879b843f98cb57c8a755aa856fb381
ms.openlocfilehash: 39b35cccf78bba4e69a7de0ca3a5a8dc516201e3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="install-cloud-based-distribution-points-in-microsoft-azure-for-system-center-configuration-manager"></a>Zainstalować punkty dystrybucji w chmurze platformy Microsoft Azure dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Punkty dystrybucji w chmurze programu System Center Configuration Manager można zainstalować w Microsoft Azure. Jeśli potrafisz z punktami dystrybucji w chmurze, zobacz [przy użyciu punktu dystrybucji w chmurze](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) przed kontynuowaniem.

 Przed rozpoczęciem instalacji upewnij się, czy masz wymagane pliki certyfikatu:  

-   Certyfikat zarządzania Microsoft Azure wyeksportowany do pliku cer lub pliku pfx.  

-   Menedżer konfiguracji chmurze certyfikat usługi punktu dystrybucji wyeksportowany do pliku pfx.  

    > [!TIP]
    >   Aby uzyskać więcej informacji na temat tych certyfikatów, zobacz sekcję dla punktów dystrybucji w chmurze w [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) tematu. Przykład wdrożenia certyfikatu usługi punktu dystrybucji w chmurze, zobacz sekcję "Wdrażanie certyfikatu usługi dla chmurowych punktów dystrybucji" w [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  


 Po zainstalowaniu punktu dystrybucji w chmurze Azure automatycznie generuje identyfikator GUID dla usługi i dodaj go do sufiksu DNS **cloudapp.net**. Przy użyciu tego identyfikatora GUID, należy skonfigurować w systemie DNS alias DNS (rekord CNAME). Dzięki temu można mapować nazwy usługi zdefiniowanej w certyfikacie usługi punktu dystrybucji w chmurze programu Configuration Manager automatycznie generowanym identyfikatorze GUID.  

 Jeśli używasz serwera proxy sieci web, może być skonfigurowanie ustawień serwera proxy w celu umożliwienia komunikacji z usługą w chmurze, który obsługuje punkt dystrybucji.  

##  <a name="BKMK_ConfigWindowsAzureandInstallDP"></a>Konfigurowanie Azure i zainstaluj punkty dystrybucji w chmurze  
 Użyj następujących procedur, aby skonfigurować Azure w celu obsługi punktów dystrybucji, a następnie zainstalować punkt dystrybucji w chmurze w programie Configuration Manager.  

### <a name="to-set-up-a-cloud-service-in-azure-for-a-distribution-point"></a>Aby skonfigurować usługi w chmurze platformy Azure dla punktu dystrybucji  

1.  Otwórz przeglądarkę sieci web do portalu Azure w https://manage.windowsazure.com, a dostęp do Twojego konta.  

2.  Kliknij przycisk **usługi hostowane, konta magazynów i CDN**, a następnie wybierz **certyfikaty zarządzania**.  

3.  Kliknij prawym przyciskiem myszy subskrypcję, a następnie wybierz **Dodaj certyfikat**.  

4.  Dla **plik certyfikatu**, określ plik cer zawierający zarządzania Azure wyeksportowany certyfikat używany dla tej usługi w chmurze, a następnie kliknij przycisk **OK**.  

Certyfikat zarządzania zostanie załadowany w systemie Azure i będzie można zainstalować punkt dystrybucji w chmurze.  

### <a name="to-install-a-cloud-based-distribution-point-for-configuration-manager"></a>Aby zainstalować punkt dystrybucji w chmurze dla programu Configuration Manager  

1.  Wykonaj kroki z poprzedniej procedury, aby skonfigurować usługi w chmurze platformy Azure z certyfikatem zarządzania.  

2.  W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usług w chmurze**i wybierz **punkty dystrybucji w chmurze**. Na **Home** , kliknij pozycję **Utwórz punkty dystrybucji w chmurze**.  

3.  Na **ogólne** strony chmury Kreatora tworzenia punktu dystrybucji, skonfigurować następujące:  

    -   Określ **identyfikator subskrypcji** konta systemu Azure.  

        > [!TIP]  
        >  Identyfikator subskrypcji Azure można znaleźć w portalu Azure.  

    -   Określ **certyfikat zarządzania**. Kliknij przycisk **Przeglądaj** do określ plik PFX zawierający wyeksportowany zarządzania Azure certyfikat, a następnie wprowadź hasło dla certyfikatu. Opcjonalnie można wybrać plik 1 .publishsettings wersja z Azure SDK 1.7.  

4.  Kliknij przycisk **Dalej**. Program Configuration Manager łączy się Azure, aby sprawdzić poprawność certyfikatu zarządzania.  

5.  Na **ustawienia** , wykonaj następujące czynności, a następnie kliknij przycisk **dalej**:  

    -   Dla **Region**, zaznacz region platformy Azure, w którym chcesz utworzyć usługę w chmurze, który obsługuje ten punkt dystrybucji.  

    -   Dla **plik certyfikatu**, określ plik PFX zawierający wyeksportowany certyfikat usługi punktu dystrybucji w chmurze programu Configuration Manager. Następnie wprowadź hasło.  

        > [!NOTE]  
        >  **Nazwa FQDN usługi** jest automatycznie wypełniane na podstawie nazwy podmiotu certyfikatu. W większości przypadków nie trzeba go edytować. Wyjątkiem są, jeśli jest używany jest certyfikat wieloznaczny w środowisku testowym. Na przykład w tym przypadku może nie określisz nazwę hosta kilka komputerów z tym samym sufiksem DNS może korzystać z certyfikatu. W tym scenariuszu podmiot certyfikatu zawiera wartość podobną do **CN =\*. contoso.com**, a Menedżer konfiguracji wyświetla komunikat o konieczności podania prawidłowej nazwy FQDN. Kliknij przycisk **OK** aby zamknąć komunikat, a następnie wprowadź określoną nazwę przed sufiksem DNS, aby podać pełną nazwę FQDN. Na przykład można dodać **clouddp1** określić pełną nazwę FQDN usługi **clouddp1.contoso.com**. Nazwa FQDN usługi musi być unikatowa w domenie i nie odpowiada żadnym urządzeniem dołączonym do domeny.  
        >   
        >  Certyfikaty wieloznaczne są obsługiwane tylko w środowiskach testowych.  

6.  Na **alerty** strony ustawione przydziały pamięci masowej, przydziały transferu i w jaki procent przydziałów ma programu Configuration Manager do generowania alertów. Następnie kliknij przycisk **Dalej**.  

7.  Ukończ pracę kreatora.  

Kreator tworzy nową usługę hostowaną dla punktu dystrybucji w chmurze. Po zamknięciu kreatora można monitorować postęp instalacji punktu dystrybucji w chmurze w konsoli programu Configuration Manager. Można również monitorować **CloudMgr.log** plik na serwerze lokacji głównej. Można monitorować udostępnianie usługi w chmurze w portalu Azure.  

> [!NOTE]  
>  Może potrwać do 30 minut udostępnienie nowego punktu dystrybucji w systemie Azure. Poniższy komunikat jest powtarzany w **CloudMgr.log** pliku aż do udostępnienia konta magazynu: **Oczekiwanie na sprawdzenie istnienia kontenera. Ponowne sprawdzenie za 10 sekund**. Następnie usługi zostało utworzone i skonfigurowane.  

 Można sprawdzić, czy instalacji punktu dystrybucji w chmurze jest wykonywane za pomocą następujących metod:  

-   W portalu Azure **wdrożenia** dla chmurowych punktów dystrybucji punktu Wyświetla stan **gotowe**.  

-   W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, **Konfiguracja hierarchii**, **chmury** węzła, punktu dystrybucji w chmurze Wyświetla stan **gotowe**.  

-   Menedżer konfiguracji Wyświetla identyfikator komunikatu o stanie **9409** dla składnika SMS_CLOUD_SERVICES_MANAGER.  

##  <a name="BKMK_ConfigDNSforCloudDPs"></a>Konfigurowanie rozpoznawania nazw dla punktów dystrybucji w chmurze  
 Klienci mogą uzyskać dostęp do punktu dystrybucji w chmurze, muszą być w stanie rozpoznać nazwę punktu dystrybucji w chmurze na adres IP, który zarządza Azure. Klienci realizują ten proces w dwóch następujących etapach:  

1.  Mapują nazwę usługi dostarczoną z certyfikatem usługi punktu dystrybucji w chmurze programu Configuration Manager nazwy FQDN usługi systemu Azure. Ta nazwa FQDN zawiera identyfikator GUID oraz sufiks DNS **cloudapp.net**. Identyfikator GUID jest generowany automatycznie po zainstalowaniu punktu dystrybucji w chmurze. Można zobaczyć pełną nazwę FQDN w portalu Azure, odwołując **adres URL witryny** na pulpicie nawigacyjnym usługi w chmurze. Przykład witryny adres URL jest **http://d1594d4527614a09b934d470.cloudapp.net**.  

2.  Rozpoznają nazwę FQDN usługi Azure z adresem IP przydzielonym przez Azure. Ten adres IP można również sprawdzić w pulpicie nawigacyjnym usługi w chmurze w portalu Azure i nosi nazwę **PUBLICZNY wirtualny adres IP (VIP)**.  

Aby zamapować nazwę usługi dostarczoną z certyfikatem usługi punktu dystrybucji w chmurze programu Configuration Manager (na przykład **clouddp1.contoso.com**) do nazwy usługi Azure FQDN (na przykład **d1594d4527614a09b934d470.cloudapp.net**), serwery DNS połączone z Internetem muszą mieć alias DNS (rekord CNAME). Klienci mogą następnie rozpoznać nazwę FQDN usługi Azure z adresem IP przy użyciu serwerów DNS w Internecie.  

##  <a name="BKMK_ConfigProxyforCloud"></a>Skonfiguruj ustawienia serwera proxy dla lokacji głównych zarządzających usługami w chmurze  
 Korzystając z usług w chmurze z programem Configuration Manager, lokacji głównej zarządzającej punktem dystrybucji w chmurze należy nawiązać portalu Azure. Łączy lokacji za pomocą **systemu** konto komputera lokacji podstawowej. To połączenie nawiązuje się za pomocą domyślnej przeglądarki sieci web na komputerze serwera lokacji głównej.  

 Na serwerze lokacji głównej zarządzającej punktem dystrybucji w chmurze należy skonfigurować ustawienia serwera proxy, aby umożliwić lokacji głównej dostęp do Internetu i Azure.  

 Poniższa procedura umożliwia skonfigurowanie ustawień serwera proxy dla serwera lokacji głównej w konsoli programu Configuration Manager.  

> [!TIP]  
>  Można również skonfigurować serwera proxy podczas instalowania na serwerze lokacji głównej nowych ról systemu lokacji za pomocą **lokacji Kreator dodawania ról systemu**.  

#### <a name="to-set-up-proxy-settings-for-the-primary-site-server"></a>Aby skonfigurować ustawienia serwera proxy dla serwera lokacji głównej  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**i kliknij pozycję **Serwery i role systemu lokacji**. Następnie wybierz serwer lokacji głównej zarządzającej punktem dystrybucji w chmurze.  

3.  W okienku szczegółów kliknij prawym przyciskiem myszy **system lokacji**, a następnie kliknij przycisk **właściwości**.  

4.  W **właściwości systemu lokacji**, wybierz opcję **serwera Proxy** karcie, a następnie skonfiguruj ustawienia serwera proxy dla serwera lokacji głównej.  

5.  Kliknij przycisk **OK** Aby zapisać ustawienia.  

