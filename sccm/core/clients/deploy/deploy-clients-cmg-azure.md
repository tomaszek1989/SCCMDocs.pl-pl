---
title: Zainstaluj klienta z usługą Azure AD
titleSuffix: Configuration Manager
description: Instalowanie i przypisać klienta programu Configuration Manager na urządzeniach z systemem Windows 10 za pomocą usługi Azure Active Directory do uwierzytelniania
ms.custom: na
ms.date: 03/28/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a44006eb-8650-49f6-94e1-18fa0ca959ee
caps.latest.revision: 14
caps.handback.revision: 0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 12fc1b394ae98c2b384630f4a00e4239e4e8d9d6
ms.sourcegitcommit: aed99ba3c5e9482199cb3fc5c92f6f3a160cb181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="install-and-assign-configuration-manager-windows-10-clients-using-azure-ad-for-authentication"></a>Zainstaluj i przypisz przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10

Aby zainstalować klienta programu Configuration Manager na urządzeniach z systemem Windows 10 przy użyciu uwierzytelniania usługi Azure AD, integracja programu Configuration Manager z usługą Azure Active Directory (Azure AD). Klienci mogą mieć w intranecie komunikują się bezpośrednio z punktu zarządzania z włączonym protokołem HTTPS. Można je również internetowy komunikacji za pośrednictwem CMG lub z punktem zarządzania internetowego. Ten proces używa usługi Azure AD do uwierzytelniania klientów do lokacji programu Configuration Manager. Usługi Azure AD zastępuje konieczność skonfigurowania i używają certyfikatów uwierzytelniania klienta.



## <a name="before-you-begin"></a>Przed rozpoczęciem

- Warunkiem wstępnym jest dzierżawa usługi Azure AD  

- Wymagania dotyczące urządzeń:  

    - Windows 10  

    - Dołączone do usługi Azure AD, czysty chmury przyłączonych do domeny lub hybrydowego Azure przyłączonych do usługi AD  

- Wymagania dotyczące użytkownika:  

    - Zalogowany użytkownik musi być tożsamością usługi Azure AD.   

    - Jeśli użytkownik jest tożsamości federacyjnych i zsynchronizowane, należy użyć programu Configuration Manager [odnajdywania użytkownika usługi Active Directory](/sccm/core/servers/deploy/configure/about-discovery-methods#bkmk_aboutUser) oraz [odnajdowanie użytkowników usługi Azure AD](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc). Aby uzyskać więcej informacji o tożsamości hybrydowej, zobacz [Definiowanie strategii wdrażania tożsamości hybrydowej](/azure/active-directory/active-directory-hybrid-identity-design-considerations-identity-adoption-strategy).<!--497750-->  

- Oprócz [istniejące warunki wstępne](/sccm/core/plan-design/configs/site-and-site-system-prerequisites#bkmk_2012MPpreq) roli systemu lokacji punktu zarządzania, należy również włączyć **ASP.NET 4.5** na tym serwerze. Zawierają inne opcje, które zostaną zaznaczone automatycznie podczas włączania ASP.NET 4.5.  

- Skonfiguruj wszystkie punkty zarządzania w trybie protokołu HTTPS. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące certyfikatu PKI](/sccm/core/plan-design/network/pki-certificate-requirements) i [wdrażania certyfikatu serwera sieci web dla systemów lokacji z usługami IIS](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012).  
    - Jeśli używasz brama zarządzania chmury, następnie wystarczy Skonfiguruj protokół HTTPS dla punktów zarządzania, umożliwiające zarządzanie bramy chmury.
    - Jeśli wdrażasz klienci w intranecie, przy użyciu uwierzytelniania opartego na tokenach usługi Azure AD, a następnie wszystkie punkty zarządzania, które mogą kontaktować się z tych klientów, należy włączyć protokół HTTPS. 

- Opcjonalne konfigurowanie [brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway) (CMG) do wdrożenia klientów internetowych. Dla lokalnych klientów, którzy uwierzytelniania za pomocą usługi Azure AD nie potrzebujesz CMG.  


## <a name="configure-azure-services-for-cloud-management"></a>Konfigurowanie usług platformy Azure do zarządzania chmurą

Połączenia tej lokacji programu Configuration Manager z usługą Azure AD jako pierwsze. Aby uzyskać szczegółowe informacje o tym procesie, zobacz [usług Azure skonfigurować](/sccm/core/servers/deploy/configure/azure-services-wizard). Utwórz połączenie **zarządzania chmurą** usługi.

Włącz [odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc) jako część procesu dołączania do **zarządzania chmurą**. 

Po wykonaniu tych czynności tej lokacji programu Configuration Manager jest połączony z usługą Azure AD. 



## <a name="configure-client-settings"></a>Konfigurowanie ustawień klienta

Te ustawienia klienta pomagają sprzężenia systemu Windows 10 urządzeń z usługą Azure AD. Umożliwiają one również klientów internetowych do korzystania z punktu dystrybucji CMG i w chmurze.

1.  Skonfiguruj następujące ustawienia klienta w **usługi w chmurze** sekcji, korzystając z informacji w [sposób konfigurowania ustawień klienta](/sccm/core/clients/deploy/configure-client-settings).  

    - **Zezwalaj na dostęp do punktu dystrybucji w chmurze**: Włącz to ustawienie ułatwić urządzeń internetowych, Pobierz zawartość wymagane do zainstalowania klienta programu Configuration Manager. Jeśli zawartość nie jest dostępna w punkcie dystrybucji w chmurze, urządzenia mogą pobierać zawartość ze CMG. Bootstrap instalacji klienta ponowi próbę punkt dystrybucji w chmurze do czterech godzin, zanim nastąpi powrót do CMG.<!--495533-->  

    - **Automatycznego rejestrowania nowych urządzeń przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory**: Ustaw **tak** lub **nr**. Ustawieniem domyślnym jest **tak**. To zachowanie jest to wartość domyślna w systemie Windows 10 w wersji 1709.

    - **Umożliwia klientom używać bramy zarządzania chmury** — ustawioną **tak** (ustawienie domyślne) lub **nr**.  

2.  Wdróż ustawienia klienta w wymaganej kolekcji urządzeń. Te ustawienia nie są wdrażane w kolekcjach użytkowników.

Aby upewnić się, urządzenie jest dołączane do usługi Azure AD, uruchom `dsregcmd.exe /status` w wierszu polecenia. **AzureAdjoined** w pokazuje wyniki **tak** Jeśli urządzenie jest przyłączonych do usługi AD platformy Azure.



## <a name="install-and-register-the-client-using-azure-ad-identity"></a>Zainstaluj i Zarejestruj klienta przy użyciu tożsamości usługi Azure AD

Aby ręcznie zainstalować klienta przy użyciu tożsamości usługi Azure AD, najpierw należy przejrzeć ogólny proces na [jak instalować klientów ręcznie](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual). 

 > [!Note]  
 > Urządzenie musi mieć dostęp do Internetu, aby skontaktować się z usługą Azure AD, ale nie musi być internetowego. 

Poniższy przykład przedstawia ogólną strukturę wiersza polecenia: `ccmsetup.exe /mp:<source management point> CCMHOSTNAME=<internet-based management point> SMSSiteCode=<site code> SMSMP=<initial management point> AADTENANTID=<Azure AD tenant identifier> AADCLIENTAPPID=<Azure AD client app identifier> AADRESOURCEURI=<Azure AD server app identifier>`

Aby uzyskać więcej informacji, zobacz [właściwości instalacji klienta](/sccm/core/clients/deploy/about-client-installation-properties).

/Mp i właściwości CCMHOSTNAME określić jedną z następujących czynności, w zależności od scenariusza:
- Punkt zarządzania lokalnymi. Określ tylko właściwości /mp. CCMHOSTNAME nie jest wymagane.
- Brama zarządzania w chmurze
- Punkt zarządzania internetowego właściwość SMSMP określa lokalnej lub w punkt zarządzania internetowego.

W tym przykładzie użyto zarządzania bramy chmury. Ta funkcja zastępuje przykładowe wartości dla każdej właściwości: `ccmsetup.exe /mp:https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC SMSMP=https://mp1.contoso.com AADTENANTID=daf4a1c2-3a0c-401b-966f-0b855d3abd1a AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver`

Aby zautomatyzować instalację klienta przy użyciu tożsamości usługi Azure AD za pomocą programu Microsoft Intune, zobacz proces [urządzenia przygotowanie systemu Windows 10 do zarządzania wspólnej](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client).



## <a name="next-steps"></a>Następne kroki

Po wykonaniu tych czynności można kontynuować [monitorowania klientów i zarządzanie nimi](/sccm/core/clients/manage/monitor-clients).
