---
title: "Instalowanie punktów dystrybucji w chmurze"
titleSuffix: Configuration Manager
description: "Dowiedz się, co należy zrobić, aby rozpocząć korzystanie z punktów dystrybucji w chmurze w systemie Microsoft Azure."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bb83ac87-9914-4a35-b633-ad070031aa6e
caps.latest.revision: "7"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 527b416c195ef43378a67bcaa726951082c09be3
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="install-cloud-based-distribution-points-in-microsoft-azure-for-system-center-configuration-manager"></a>Instalowanie punktów dystrybucji w chmurze w systemie Microsoft Azure dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Punkty dystrybucji w chmurze programu System Center Configuration Manager można zainstalować w systemie Microsoft Azure. Jeśli znasz punkty dystrybucji w chmurze, zobacz [użycia punktu dystrybucji w chmurze](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) przed kontynuowaniem.

 Przed rozpoczęciem instalacji upewnij się, że masz wymagane pliki certyfikatu:  

-   Certyfikat zarządzania Microsoft Azure wyeksportowany do pliku .cer i do pliku .pfx.  

-   Configuration Manager oparta na chmurze certyfikat usługi punktu dystrybucji wyeksportowany do pliku .pfx.  

    > [!TIP]
    >   Aby uzyskać więcej informacji na temat tych certyfikatów, zobacz sekcję dla punktów dystrybucji w chmurze w [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md) tematu. Przykład wdrożenia certyfikatu usługi punktu dystrybucji w chmurze, w sekcji "Wdrażanie certyfikatu usługi dla chmurowych punktów dystrybucji" w [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  


 Po zainstalowaniu punktu dystrybucji w chmurze Azure automatycznie generuje identyfikator GUID dla usługi i dodaje go do sufiksu DNS **cloudapp.net**. Przy użyciu tego identyfikatora GUID, użytkownik musi skonfigurować w systemie DNS alias DNS (rekord CNAME). Dzięki temu można odwzorowania nazwy usługi zdefiniowanej w certyfikacie usługi punktu dystrybucji w chmurze programu Configuration Manager w automatycznie generowanym identyfikatorze GUID.  

 Jeśli używasz serwera proxy sieci web, może być skonfigurowanie ustawień serwera proxy w celu umożliwienia komunikacji z usługą w chmurze, który hostuje punkt dystrybucji.  

##  <a name="BKMK_ConfigWindowsAzureandInstallDP"></a>Skonfiguruj Azure i zainstaluj punkty dystrybucji w chmurze  
 Użyj następujących procedur, aby skonfigurować Azure w celu obsługi punktów dystrybucji, a następnie zainstalować punkt dystrybucji w chmurze w programie Configuration Manager.  

### <a name="to-set-up-a-cloud-service-in-azure-for-a-distribution-point"></a>Aby skonfigurować usługi w chmurze na platformie Azure dla punktu dystrybucji  

1.  Otwórz przeglądarkę sieci web do portalu Azure w https://manage.windowsazure.com, a dostęp do tego konta.  

2.  Kliknij przycisk **usługi hostowane, konta magazynów i CDN**, a następnie wybierz **certyfikaty zarządzania**.  

3.  Kliknij prawym przyciskiem myszy subskrypcję, a następnie wybierz **Dodaj certyfikat**.  

4.  Aby uzyskać **plik certyfikatu**, określ plik cer zawierający certyfikat zarządzania platformy Azure wyeksportowany do tej usługi w chmurze, a następnie kliknij przycisk **OK**.  

Certyfikat zarządzania zostanie załadowany na platformie Azure i będzie można zainstalować punktu dystrybucji w chmurze.  

### <a name="to-install-a-cloud-based-distribution-point-for-configuration-manager"></a>Aby zainstalować punkt dystrybucji w chmurze programu Configuration Manager  

1.  Wykonaj kroki opisane w poprzedniej procedury, aby skonfigurować usługi w chmurze na platformie Azure z certyfikatem zarządzania.  

2.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usługi w chmurze**i wybierz **punkty dystrybucji w chmurze**. Na **Home** , kliknij pozycję **Utwórz punkty dystrybucji w chmurze**.  

3.  Na **ogólne** strony chmury Kreatora tworzenia punktu dystrybucji, skonfiguruj następujące:  

    -   Określ **identyfikator subskrypcji** dla konta platformy Azure.  

        > [!TIP]  
        >  Identyfikator subskrypcji platformy Azure można znaleźć w portalu Azure.  

    -   Określ **certyfikat zarządzania**. Kliknij przycisk **Przeglądaj** Aby określić zawierający certyfikat zarządzania platformy Azure wyeksportowany plik PFX, a następnie wprowadź hasło dla certyfikatu. Opcjonalnie można określić wersji pliku 1 .publishsettings z zestawu Azure SDK 1.7.  

4.  Kliknij przycisk **Dalej**. Łączy się Azure, aby zweryfikować certyfikat zarządzania z programu Configuration Manager.  

5.  Na **ustawienia** , wykonaj następujące czynności, a następnie kliknij przycisk **dalej**:  

    -   Aby uzyskać **Region**, wybierz region platformy Azure, w którym ma zostać utworzona usługa w chmurze hostująca ten punkt dystrybucji.  

    -   Aby uzyskać **plik certyfikatu**, określ plik PFX zawierający wyeksportowany certyfikat dla usługi punktu dystrybucji w chmurze programu Configuration Manager. Następnie wprowadź hasło.  

        > [!NOTE]  
        >  **Nazwa FQDN usługi** pole jest wypełniane automatycznie na podstawie nazwy podmiotu certyfikatu. W większości przypadków nie trzeba go edytować. Wyjątek stanowi, jeśli używasz certyfikat wieloznaczny w środowisku testowym. Na przykład w tym przypadku może określisz nazwę hosta, dzięki czemu wiele komputerów, które mają sufiks DNS dla tego samego certyfikatu można użyć. W tym scenariuszu podmiot certyfikatu zawiera wartość podobną do **CN =\*. contoso.com**, i programu Configuration Manager wyświetla komunikat o konieczności podania prawidłowej nazwy FQDN. Kliknij przycisk **OK** aby zamknąć komunikat, a następnie wprowadź określoną nazwę przed sufiksem DNS, aby podać pełną nazwę FQDN. Na przykład można dodać **clouddp1** Aby określić pełną nazwę FQDN usługi **clouddp1.contoso.com**. Nazwa FQDN usługi musi być unikatowa w domenie i nie zgodna z żadnym urządzeniem przyłączonych do domeny.  
        >   
        >  Certyfikaty wieloznaczne są obsługiwane tylko w środowiskach testowych.  

6.  Na **alerty** strony ustawione przydziały pamięci masowej, przydziały transferu i w jaki procent przydziałów ma programu Configuration Manager do generowania alertów. Następnie kliknij przycisk **Dalej**.  

7.  Ukończ pracę kreatora.  

Kreator tworzy nową usługę hostowaną dla punktu dystrybucji w chmurze. Po zamknięciu kreatora można monitorować postęp instalacji punktu dystrybucji w chmurze w konsoli programu Configuration Manager. Można również monitorować **CloudMgr.log** pliku na serwerze lokacji głównej. Można monitorować udostępnianie usługi w chmurze w portalu Azure.  

> [!NOTE]  
>  Może upłynąć do 30 minut udostępnienie nowego punktu dystrybucji na platformie Azure. Poniższy komunikat jest powtarzany w **CloudMgr.log** pliku do momentu aprowizacji konta magazynu: **Oczekiwanie na sprawdzenie istnienia kontenera. Ponowne sprawdzenie za 10 sekund**. Następnie usługa jest utworzony i skonfigurowany.  

 Można określić, że instalacja punktu dystrybucji w chmurze zakończyło się przy użyciu następujących metod:  

-   W portalu Azure **wdrożenia** dla chmurowych punktów dystrybucji punktu Wyświetla stan **gotowe**.  

-   W konsoli programu Configuration Manager w **administracji** roboczym **Konfiguracja hierarchii**, **chmury** węzła, punktu dystrybucji w chmurze Wyświetla stan **gotowe**.  

-   Menedżer konfiguracji Wyświetla identyfikator komunikatu o stanie **9409** dla składnika SMS_CLOUD_SERVICES_MANAGER.  

##  <a name="BKMK_ConfigDNSforCloudDPs"></a>Konfigurowanie rozpoznawania nazw dla punktów dystrybucji w chmurze  
 Zanim klienci mogą uzyskać dostęp do punktu dystrybucji w chmurze, muszą być w stanie rozpoznać nazwę punktu dystrybucji w chmurze na adres IP, która zarządza Azure. Klienci to zrobić na dwa etapy:  

1.  Mapują nazwę usługi dostarczoną z certyfikatem usługi punktu dystrybucji w chmurze programu Configuration Manager do nazwy FQDN usługi platformy Azure. Ta nazwa FQDN zawiera identyfikator GUID oraz sufiks DNS **cloudapp.net**. Identyfikator GUID jest generowany automatycznie po zainstalowaniu punktu dystrybucji w chmurze. Można zobaczyć pełną nazwę FQDN w portalu Azure, odwołując **adres URL witryny** na pulpicie nawigacyjnym usługi w chmurze. Przykład witryny adres URL jest **http://d1594d4527614a09b934d470.cloudapp.net**.  

2.  Rozpoznają nazwę FQDN usługi platformy Azure na adres IP, który przydziela Azure. Ten adres IP można również sprawdzić w pulpicie nawigacyjnym usługi w chmurze w portalu Azure i nosi nazwę **PUBLICZNY wirtualny adres IP (VIP)**.  

Aby zamapować nazwę usługi dostarczoną z certyfikatem usługi punktu dystrybucji w chmurze programu Configuration Manager (na przykład **clouddp1.contoso.com**) do platformy Azure nazwę FQDN usługi (na przykład **d1594d4527614a09b934d470.cloudapp.net**), serwery DNS w Internecie muszą mieć alias DNS (rekord CNAME). Klienci mogą następnie rozpoznać nazwę FQDN usługi platformy Azure z adresem IP przy użyciu serwerów DNS w Internecie.  

##  <a name="BKMK_ConfigProxyforCloud"></a>Konfigurowanie ustawień serwera proxy dla lokacji głównych zarządzających usługami w chmurze  
 Korzystając z usługi w chmurze z programem Configuration Manager, lokacji głównej zarządzającej punktem dystrybucji w chmurze musi być można nawiązać połączenia z portalu Azure. Łączy lokacji za pomocą **systemu** konto komputera lokacji głównej. To połączenie jest nawiązywane za pomocą domyślnej przeglądarki sieci web na komputerze serwera lokacji głównej.  

 Na serwerze lokacji głównej zarządzającej punktem dystrybucji w chmurze może być można skonfigurować ustawienia serwera proxy, aby umożliwić lokacji głównej dostęp do Internetu oraz platformy Azure.  

 Aby skonfigurować ustawienia serwera proxy dla serwera lokacji głównej w konsoli programu Configuration Manager, należy użyć następującej procedury.  

> [!TIP]  
>  Można również skonfigurować serwera proxy podczas instalowania nowych ról systemu lokacji na serwerze lokacji głównej przy użyciu **lokacji Kreator dodawania ról systemu**.  

#### <a name="to-set-up-proxy-settings-for-the-primary-site-server"></a>Aby skonfigurować ustawienia serwera proxy dla serwera lokacji głównej  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**i kliknij pozycję **Serwery i role systemu lokacji**. Następnie wybierz serwer lokacji głównej zarządzającej punktem dystrybucji w chmurze.  

3.  W okienku szczegółów kliknij prawym przyciskiem myszy **system lokacji**, a następnie kliknij przycisk **właściwości**.  

4.  W **właściwości systemu lokacji**, wybierz pozycję **Proxy** karcie, a następnie skonfigurować ustawienia serwera proxy dla serwera lokacji głównej.  

5.  Kliknij przycisk **OK** Aby zapisać ustawienia.  
