---
title: Instalowanie i przypisania klienta z Internetu | Dokumentacja firmy Microsoft
description: "Zainstaluj i przypisać klienta programu System Center Configuration Manager z Internetu."
ms.custom: na
ms.date: 7/31/2017
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
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: f604557d208b2dda9dc1c6b4c4d27d896d47695e
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---

# <a name="install-and-assign-configuration-manager-clients-from-the-internet-using-azure-ad-for-authentication"></a>Zainstaluj i przypisz z Internetu przy użyciu usługi Azure AD do uwierzytelniania klientów programu Configuration Manager

Usługi w chmurze programu Configuration Manager z usługą Azure AD umożliwia obsługuje następujące scenariusze:

- Ręcznie zainstaluj klienta programu Configuration Manager z Internetu i jego przypisania do lokacji programu Configuration Manager (wymaga roli systemu lokacji chmury zarządzania bramy).
- Przy użyciu usługi Azure AD do uwierzytelniania klientów w Internecie, aby uzyskać dostęp z lokacji programu Configuration Manager. Usługi Azure AD zastępuje konieczność skonfigurowania i używają certyfikatów uwierzytelniania klienta.
- Odnajdywanie użytkowników usługi Azure AD do witryny do użycia w kolekcji i innych operacji programu Configuration Manager.

Aby to zrobić, wykonaj następujące kroki:

- **Krok 1. Skonfiguruj bramę zarządzania w chmurze**
- **Krok 2. Konfigurowanie aplikacji usługi Azure Configuration Manager usług w chmurze**
- **Krok 3. Konfigurowanie ustawień klienta do rejestracji urządzeń z systemem Windows 10 z usługą Azure AD**
- **Krok 4. Zainstaluj i Zarejestruj klienta programu Configuration Manager za pomocą usługi Azure Active Directory tożsamości**


## <a name="before-you-start"></a>Przed rozpoczęciem

- Musi mieć dzierżawa usługi Azure AD.
- Urządzenia muszą systemem Windows 10 i być usługi Azure AD przyłączony. Klientów można też Ponadto przyłączony do usługi Azure AD przyłączonych do domeny).
- Oprócz [istniejące warunki wstępne](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) roli systemu lokacji punktu zarządzania, należy również upewnić się, że **ASP.NET 4.5** (i innych automatycznie wybieranych opcji) są włączone na komputerze, który hostuje tę rolę systemu lokacji.
- Na potrzeby wdrożenia klienta programu Configuration Manager:
    - Skonfiguruj co najmniej jeden punkt zarządzania w trybie protokołu HTTPS.
    - Skonfiguruj bramę zarządzania chmury.

## <a name="step-1-set-up-the-cloud-management-gateway"></a>Krok 1. Skonfiguruj bramę zarządzania w chmurze

Skonfiguruj bramę zarządzania chmury, aby umożliwić klientom dostęp do tej lokacji programu Configuration Manager z Internetu bez korzystania z certyfikatów. Pomoc można znaleźć w następujących tematach: 

- [Planowanie brama zarządzania chmury w programie Configuration Manager](/sccm/core/clients/manage/plan-cloud-management-gateway).
- [Konfigurowanie bramy zarządzania w chmurze programu Configuration Manager](/sccm/core/clients/manage/setup-cloud-management-gateway).
- [Brama zarządzania Monitor chmury w programie Configuration Manager](/sccm/core/clients/manage/monitor-clients-cloud-management-gateway).

## <a name="step-2-set-up-the-azure-services-app-in-configuration-manager-cloud-services"></a>Krok 2. Konfigurowanie aplikacji usługi Azure Configuration Manager usług w chmurze

Łączy z tej lokacji programu Configuration Manager z usługą Azure AD i jest wymaganiem wstępnym dla wszystkich operacji w tej sekcji. 

Odnajdowanie użytkowników usługi Azure AD jest skonfigurowany jako część *zarządzania chmurą*. Procedury w tym celu została szczegółowo opisana w kroku **6** procedury [tworzenie aplikacji sieci web platformy Azure do użytku w programie Configuration Manager](/sccm/core/servers/deploy/configure/Azure-services-wizard#webapp) w temacie *usług Azure skonfigurować do użytku z programem Configuration Manager*.
    
Po zakończeniu procedury połączeniu lokacji programu Configuration Manager z usługą Azure AD. 

## <a name="step-3-configure-client-settings-to-register-windows-10-devices-with-azure-ad"></a>Krok 3. Konfigurowanie ustawień klienta do rejestracji urządzeń z systemem Windows 10 z usługą Azure AD

1.  Skonfiguruj w poniższej sekcji (znalezione w usługach chmury) ustawienia klienta, korzystając z informacji w [sposób konfigurowania ustawień klienta](/sccm/core/clients/deploy/configure-client-settings).
    - **Automatycznego rejestrowania nowych urządzeń przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory** — ustawioną **tak** (ustawienie domyślne) lub **nr**.
    - **Umożliwia klientom używać bramy zarządzania chmury** — ustawioną **tak** (ustawienie domyślne) lub **nr**.
2.  Wdróż ustawienia klienta w wymaganej kolekcji urządzeń.

Aby upewnić się, że urządzenie jest dołączane do usługi Azure AD, uruchom polecenie **/status dsregcmd.exe** w oknie wiersza polecenia. **AzureAdjoined** w pokazuje wyniki **tak** Jeśli urządzenie jest usługi Azure AD przyłączony.


## <a name="step-4-install-and-register-the-configuration-manager-client-using-azure-active-directory-identity"></a>Krok 4. Zainstaluj i Zarejestruj klienta programu Configuration Manager za pomocą usługi Azure Active Directory tożsamości

Przed rozpoczęciem upewnij się, że pliki źródłowe instalacji klienta są przechowywane lokalnie na urządzeniu, z którym chcesz zainstalować klienta. Następnie postępuj zgodnie z instrukcjami w [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#a-namebkmkmanuala-how-to-install-clients-manually) przy użyciu następującego wiersza polecenia instalacji: 

**ccmsetup.exe nocrlcheck /Source:C:\CLIENT CCMHOSTNAME=SCCMPROXYCONTOSO.CLOUDAPP.NET/CCM_Proxy_ServerAuth/72457598037527932 SMSSiteCode = HEC AADTENANTID = AADTENANTNAME 780433B5-E05E-4B7D-BFD1-E8013911E543 = contoso AADCLIENTAPPID = AADRESOURCEURI = https://contososerver**

- **/ NoCrlCheck:** Jeśli punkt zarządzania infrastrukturą lub w chmurze brama zarządzania używa certyfikatu serwera niepubliczne, następnie klienta może nie być możliwe nawiązanie łączności lokalizacja listy CRL.
- **/ Źródło:** Folder lokalny: Lokalizacja plików instalacyjnych klienta.
- **CCMHOSTNAME:** Nazwa punktu zarządzania z Internetu. Można go znaleźć, uruchamiając **gwmi root\ccm\locationservices - namespace-klasy SMS_ActiveMPCandidate** w wierszu polecenia na komputerze klienckim zarządzanych.
- **SMSMP:** Nazwa wyszukiwania punktu zarządzania — punkt zarządzania może być w sieci intranet.
- **SMSSiteCode:** Kod lokacji w lokacji programu Configuration Manager.
- **AADTENANTID:**, **AADTENANTNAME:** Identyfikator i nazwa dzierżawy usługi Azure AD jest połączony do programu Configuration Manager. Można okaże się, że to uruchamiając/status dsregcmd.exe z wiersza polecenia w usłudze Azure AD przyłączone do urządzenia.
- **AADCLIENTAPPID:** Identyfikator aplikacji klienta usługi Azure AD. Aby uzyskać pomoc, to wyszukiwanie, [użycia portalu do tworzenia aplikacji i usług podmiot zabezpieczeń, który ma dostęp do zasobów usługi Azure Active Directory](https://docs.microsoft.com/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key).
- **AADResourceUri:** Identyfikator URI serwera aplikacji został załadowany w usłudze Azure AD.


## <a name="next-steps"></a>Następne kroki

Po wykonaniu tych czynności można kontynuować [monitorowania klientów i zarządzanie nimi](/sccm/core/clients/manage/monitor-clients).

