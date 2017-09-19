---
title: Instalowanie i przypisania klienta z Internetu | Dokumentacja firmy Microsoft
description: "Zainstaluj i przypisać klienta programu System Center Configuration Manager z Internetu."
ms.custom: na
ms.date: 8/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a44006eb-8650-49f6-94e1-18fa0ca959ee
caps.latest.revision: "14"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: d783cc2f12400084ad1cd62a338a31c9747c05fb
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="install-and-assign-configuration-manager-windows-10-clients-using-azure-ad-for-authentication"></a>Zainstaluj i przypisz przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager systemu Windows 10

Usługi w chmurze programu Configuration Manager z usługą Azure AD umożliwia obsługuje następujące scenariusze:

- Ręcznie zainstaluj klienta programu Configuration Manager na urządzeniach z systemem Windows 10 z Internetu, a jego przypisania do lokacji programu Configuration Manager (wymaga roli systemu lokacji chmury zarządzania bramy).
- Przy użyciu usługi Azure AD do uwierzytelniania klientów do lokacji programu Configuration Manager. Usługi Azure AD zastępuje konieczność skonfigurowania i używają certyfikatów uwierzytelniania klienta.
- Odnajdywanie użytkowników usługi Azure AD do witryny do użycia w kolekcji i innych operacji programu Configuration Manager.

Aby to zrobić, wykonaj następujące kroki:

- **Krok 1. Konfigurowanie aplikacji usługi Azure w usługi w chmurze programu Configuration Manager i skonfigurować odnajdowanie użytkowników usługi AD platformy Azure**
- **Krok 2. Skonfiguruj bramę zarządzania chmury** (opcjonalny w przypadku klientów lokalnych)
- **Krok 3. Konfigurowanie ustawień klienta przyłączanie się do urządzeń z systemem Windows 10 z usługą Azure AD i umożliwić klientom używanie brama zarządzania w chmurze**
- **Krok 4. Zainstaluj i Zarejestruj klienta programu Configuration Manager za pomocą usługi Azure Active Directory tożsamości**


## <a name="before-you-start"></a>Przed rozpoczęciem

- Musi mieć dzierżawa usługi Azure AD.
- Urządzenia należy uruchomić Windows 10 można usługi Azure AD przyłączony i zalogować się przy użyciu tożsamości usługi Azure AD. Klientów można też Ponadto przyłączony do usługi Azure AD przyłączonych do domeny).
- Oprócz [istniejące warunki wstępne](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) roli systemu lokacji punktu zarządzania, należy również upewnić się, że **ASP.NET 4.5** (i innych automatycznie wybieranych opcji) są włączone na komputerze, który hostuje tę rolę systemu lokacji.
- Na potrzeby wdrożenia klienta programu Configuration Manager:
    - Jeśli chcesz używać usługi Azure AD na potrzeby uwierzytelniania zamiast certyfikaty klienta, należy skonfigurować co najmniej jeden punkt zarządzania w trybie protokołu HTTPS.
        Jeśli używane są certyfikaty klienta zamiast chmury brama zarządzania, punkt zarządzania HTTPS jest opcjonalna, ale zalecana. Jeśli używasz usługi Azure AD na potrzeby uwierzytelniania, czy dla na lokalnym lub klientów internetowych, punkt zarządzania HTTPS jest wymagana.
    - Skonfiguruj bramę zarządzania chmury, jeśli chcesz wdrożyć klientów internetowych. Dla lokalnych klientów, którzy są uwierzytelniani w usłudze Azure AD, nie należy skonfigurować bramę zarządzania chmury.


## <a name="step-1-set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>Krok 1. Konfigurowanie aplikacji usługi Azure Configuration Manager usług w chmurze

Łączy z tej lokacji programu Configuration Manager z usługą Azure AD i jest wymaganiem wstępnym dla wszystkich operacji w tej sekcji. 

Odnajdowanie użytkowników usługi Azure AD jest skonfigurowany jako część *zarządzania chmurą*. Procedury w tym celu została szczegółowo opisana w kroku **6** procedury [tworzenie aplikacji sieci web platformy Azure do użytku w programie Configuration Manager](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) w temacie *usług Azure skonfigurować do użytku z programem Configuration Manager*.
    
Po zakończeniu procedury połączeniu lokacji programu Configuration Manager z usługą Azure AD. 

## <a name="step-2-set-up-the-cloud-management-gateway"></a>Krok 2. Skonfiguruj bramę zarządzania w chmurze

Konfigurowanie bramy zarządzania chmury dzięki temu scenariusze zarządzania chmury, które są opisane w tym temacie. Pomoc można znaleźć w następujących tematach: 

- [Planowanie brama zarządzania chmury w programie Configuration Manager](/sccm/core/clients/manage/plan-cloud-management-gateway).
- [Konfigurowanie bramy zarządzania w chmurze programu Configuration Manager](/sccm/core/clients/manage/setup-cloud-management-gateway).
- [Brama zarządzania Monitor chmury w programie Configuration Manager](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway).

## <a name="step-3-configure-client-settings-to-join-windows-10-devices-with-azure-ad-and-enable-clients-to-use-the-cloud-management-gateway"></a>Krok 3. Konfigurowanie ustawień klienta przyłączanie się do urządzeń z systemem Windows 10 z usługą Azure AD i umożliwić klientom używanie brama zarządzania w chmurze

1.  Skonfiguruj następujące ustawienia klienta (w **usługi w chmurze**) sekcji, korzystając z informacji w [sposób konfigurowania ustawień klienta](/sccm/core/clients/deploy/configure-client-settings).
    - **Zezwalaj na dostęp do punktu dystrybucji w chmurze** — to ustawienie ułatwić urządzeń internetowych, aby uzyskać zawartość wymagane do zainstalowania klienta programu Configuration Manager. Jeśli zawartość nie jest dostępna w punkcie dystrybucji w chmurze, urządzenia można pobrać zawartości z punktu zarządzania połączony z bramą zarządzania w chmurze.
    - **Automatycznego rejestrowania nowych urządzeń przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory** — ustawioną **tak** (ustawienie domyślne) lub **nr**.
    - **Umożliwia klientom używać bramy zarządzania chmury** — ustawioną **tak** (ustawienie domyślne) lub **nr**.
2.  Wdróż ustawienia klienta w wymaganej kolekcji urządzeń. Te ustawienia nie są wdrażane w kolekcjach użytkowników.

Aby upewnić się, że urządzenie jest dołączane do usługi Azure AD, uruchom polecenie **/status dsregcmd.exe** w oknie wiersza polecenia. **AzureAdjoined** w pokazuje wyniki **tak** Jeśli urządzenie jest usługi Azure AD przyłączony.


## <a name="step-4-install-and-register-the-configuration-manager-client-using-azure-active-directory-identity"></a>Krok 4. Zainstaluj i Zarejestruj klienta programu Configuration Manager za pomocą usługi Azure Active Directory tożsamości

Aby zainstalować klienta, skorzystaj z instrukcji w [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually) przy użyciu następującego wiersza polecenia instalacji: 

**ccmsetup.exe /mp &#58; https://contoso.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057594037928100 CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode = DPD SMSMP = https://SCCMDFPSS.contoso.corp.contoso.com AADTENANTID = AADTENANTNAME 72F988BF-86F1-41AF-91AB-2D7CD011DB47 = contoso AADCLIENTAPPID = AADRESOURCEURI bef323b3-042f-41a6-907a-f9faf0d17026 = https://contososerver**

- **/MP** — źródło pobierania. Można ustawić CMG Jeśli bootstrap z Internetu.
- **CCMHOSTNAME:** Nazwa punktu zarządzania z Internetu. Można go znaleźć, uruchamiając **gwmi root\ccm\locationservices - namespace-klasy SMS_ActiveMPCandidate** w wierszu polecenia na komputerze klienckim zarządzanych.
- **SMSSiteCode:** Kod lokacji w lokacji programu Configuration Manager.
- **SMSMP:** Nazwa wyszukiwania punktu zarządzania — punkt zarządzania może być w sieci intranet.
- **AADTENANTID:**, **AADTENANTNAME:** Identyfikator i nazwa dzierżawy usługi Azure AD jest połączony do programu Configuration Manager. Można okaże się, że to uruchamiając/status dsregcmd.exe z wiersza polecenia w usłudze Azure AD przyłączone do urządzenia.
- **AADCLIENTAPPID:** Identyfikator aplikacji klienta usługi Azure AD. Aby uzyskać pomoc, to wyszukiwanie, [użycia portalu do tworzenia aplikacji i usług podmiot zabezpieczeń, który ma dostęp do zasobów usługi Azure Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key).
- **AADResourceUri:** Identyfikator URI serwera aplikacji został załadowany w usłudze Azure AD. Aby uzyskać więcej informacji, zobacz [usług Azure skonfigurować do użytku z programem Configuration Manager](/sccm/core/servers/deploy/configure/azure-services-wizard).




## <a name="next-steps"></a>Następne kroki

Po wykonaniu tych czynności można kontynuować [monitorowania klientów i zarządzanie nimi](/sccm/core/clients/manage/monitor-clients).
