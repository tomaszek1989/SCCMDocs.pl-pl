---
title: Jednoczesne zarządzania dla urządzeń z systemem Windows 10
titleSuffix: Configuration Manager
description: Dowiedz się, jak jednocześnie zarządzać urządzeniami z systemem Windows 10, używając programu Configuration Manager i Microsoft Intune.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/28/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology: ''
ms.assetid: d6bbc787-83a5-44b4-ad64-016e5da7413f
ms.openlocfilehash: cda2ef22bbfb86d0c25c44d5b97b0e1551010374
ms.sourcegitcommit: aed99ba3c5e9482199cb3fc5c92f6f3a160cb181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2018
---
# <a name="co-management-for-windows-10-devices"></a>Jednoczesne zarządzania dla urządzeń z systemem Windows 10    
<!-- 1350871 -->
Wielu klientów chcesz zarządzać urządzeniami z systemem Windows 10 w taki sam sposób ich zarządzania urządzeniami przenośnymi za pomocą uproszczonego, ekonomiczne, oparte na chmurze rozwiązanie. Jednak przejścia z tradycyjnego zarządzania do zarządzania nowoczesnymi może być trudne. W poprzednich aktualizacje systemu Windows 10, urządzenia z systemem Windows 10 można już dołączyć do lokalnej usługi Active Directory (AD) i oparta na chmurze usługi Azure AD, w tym samym czasie (rozwiązanie hybrydowe usługi Azure AD). Począwszy od programu Configuration Manager w wersji 1710 wspólnej zarządzania korzysta z tego ulepszenia i umożliwia jednocześnie Zarządzanie systemem Windows 10 wersji 1709 (znanej także jako aktualizacja twórców spadek) urządzenia, używając programu Configuration Manager i usługi Intune. To rozwiązanie, które zapewnia mostek z tradycyjnego zarządzania nowoczesnymi i umożliwia ścieżki do dokonania zmiany przy użyciu podejście etapowe. 

Istnieją dwa główne ścieżki do wspólnego zarządzania.  Jedna jest inicjowana zarządzania wspólnej gdzie przyłączone do urządzeń z systemem Windows 10 zarządzane przez program Configuration Manager i hybrydowe usługi Azure AD zarejestrować się w usłudze Intune w programie Configuration Manager. Druga to Intune zainicjowano obsługę administracyjną urządzeń, które są zarejestrowane w usłudze Intune, a następnie instalowany z zasięgu klienta programu Configuration Manager stanu zarządzania wspólnej.

## <a name="prerequisites"></a>Wymagania wstępne
Musi mieć następujące wymagania wstępne w miejscu, aby można było włączyć zarządzania wspólnej. Istnieją ogólne wymagania wstępne i inne wymagania wstępne dla urządzeń z klientem programu Configuration Manager i urządzeń, które nie mają zainstalowanego klienta.

> [!IMPORTANT]
> Urządzenia przenośne z systemem Windows 10 nie obsługują zarządzania wspólnej.

### <a name="general-prerequisites"></a>Ogólne wymagania wstępne
Poniżej przedstawiono ogólne wymagania wstępne, aby włączyć zarządzanie wspólnej:  

- Configuration Manager w wersji 1710 lub nowszy
- Azure AD
- Licencji pakietu EMS lub usługi Intune dla wszystkich użytkowników
- [Automatyczne rejestrowanie usługi Azure AD](https://docs.microsoft.com/intune/windows-enroll#enable-windows-10-automatic-enrollment) włączone
- Subskrypcję usługi Intune &#40;ustaw urząd zarządzania urządzeniami Przenośnymi w usłudze Intune **usługi Intune**&#41;


   > [!Note]  
   > Jeśli masz środowiska hybrydowego zarządzania urządzeniami Przenośnymi (usługa Intune zintegrowana z programem Configuration Manager), nie można włączyć zarządzania wspólnej. Jednak można rozpocząć migrację użytkowników do autonomicznej usługi Intune, a następnie włącz swoje skojarzone urządzenia systemu Windows 10 do zarządzania wspólnej. Aby uzyskać więcej informacji na temat migracji do autonomicznej usługi Intune, zobacz [rozpocząć migrację z hybrydowego zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

### <a name="additional-prerequisites-for-devices-with-the-configuration-manager-client"></a>Dodatkowe wymagania wstępne dotyczące urządzeń z klientem programu Configuration Manager
- Windows 10, wersja 1709 (znanej także jako aktualizacja twórców spadek) lub nowszy
- [Przyłączony do hybrydowej usługi Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) (dołączony do usługi AD i Azure AD)

### <a name="additional-prerequisites-for-devices-without-the-configuration-manager-client"></a>Dodatkowe wymagania wstępne dotyczące urządzeń bez klienta programu Configuration Manager
- Windows 10, wersja 1709 (znanej także jako aktualizacja twórców spadek) lub nowszy
- [Brama zarządzania w chmurze](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) w programie Configuration Manager (Jeśli używasz usługi Intune, aby zainstalować klienta programu Configuration Manager)

## <a name="workloads-you-can-switch-to-intune"></a>Obciążenia można przełączyć się do usługi Intune
Po włączeniu wspólnego zarządzania programu Configuration Manager nadal zarządza wszystkich obciążeń. W przypadku podjęcia decyzji, że wszystko będzie gotowe, program może rozpocząć zarządzanie obciążeń dostępności usługi Intune. Może mieć następujące obciążenia zarządzania usługi Intune:   

### <a name="compliance-policies"></a>Zasady zgodności
Zasady zgodności definiują reguły i ustawienia, które urządzenie musi spełniać, aby można je było uważać za spełniające zasady dostępu warunkowego. Zasady zgodności mogą być również wykorzystane do monitorowania i rozwiązywania problemów ze zgodnością urządzeń niezależnie od dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [zasady zgodności urządzeń](/sccm/mdm/deploy-use/device-compliance-policies).  

### <a name="windows-update-for-business-policies"></a>Usługi Windows Update dla firm zasad
Windows Update dla firm, zasady umożliwiają konfigurowanie zasad odroczenia aktualizacje funkcji systemu Windows 10 lub jakości aktualizacje dla urządzeń z systemem Windows 10 zarządzanych bezpośrednio przez usługę Windows Update dla firm. Aby uzyskać więcej informacji, zobacz [skonfigurować usługi Windows Update dla firm odroczenia zasad](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies).  

### <a name="resource-access-policies"></a>Zasady dostępu do zasobów
Zasady dostępu do zasobów skonfigurować sieci VPN, Wi-Fi, poczty e-mail i ustawienia certyfikatów na urządzeniach. Aby uzyskać więcej informacji, zobacz [wdrażania profilów dostępu do zasobów](/sccm/protect/deploy-use/deploy-wifi-vpn-email-cert-profiles).

### <a name="endpoint-protection"></a>Program Endpoint Protection 
<!-- 1357365 -->
Począwszy od programu Configuration Manager 1802 obciążenia programu Endpoint Protection może zostać przeniesieni do usługi Intune. Aby uzyskać więcej informacji, zobacz [obciążenia mógł zostać przeniesieni do usługi Intune](/sccm/core/clients/manage/co-management-switch-workloads.md#Workloads-able-to-be-transitioned-to-Intune) i [programu Endpoint Protection w programie Configuration Manager](/sccm/protect/deploy-use/endpoint-protection).

## <a name="architectural-overview-for-co-management"></a>Omówienie architektury zarządzania wspólnej
Następujący diagram zawiera omówienie architektury wspólnego zarządzania i jego miejsce w istniejącej infrastruktury konfiguracji i usługi Intune.

![Diagram architektury zarządzania wspólnej](./media/co-management-arch.svg)

## <a name="scenarios-to-enable-co-management"></a>Scenariusze umożliwiające zarządzanie wspólnej  
Umożliwiają jednoczesne zarządzanie zarówno na urządzeniach z systemem Windows 10 zarejestrowanych w programie Microsoft Intune i istniejących klientów systemu Windows 10 Configuration Manager. Oba scenariusze spowodować urządzeń z systemem Windows 10 jednocześnie zarządzane przez program Configuration Manager i usługi Intune, jak również do usługi AD i Azure AD.  

### <a name="devices-enrolled-in-intune"></a>Urządzenia zarejestrowane w usłudze Intune  
W przypadku urządzeń z systemem Windows 10 zarejestrowanych w usłudze Intune, aby przygotować klientów do wspólnego zarządzania można zainstalować klienta programu Configuration Manager na urządzeniach (przy użyciu określonego argumentu wiersza polecenia). Następnie możesz włączyć zarządzanie wspólnej z konsoli programu Configuration Manager pomyśleć konkretnych obciążeń do usługi Intune dla konkretnych urządzeń z systemem Windows 10.  

Dla urządzeń z systemem Windows 10, które nie zostały jeszcze zarejestrowane w usłudze Intune można użyć automatycznego rejestrowania na platformie Azure rejestracji urządzeń. W przypadku nowych urządzeń z systemem Windows 10, można użyć [Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot) skonfigurować poza (tryb OOBE Box Experience), w tym automatycznego rejestrowania, który umożliwia rejestrację urządzeń w usłudze Intune.  

### <a name="configuration-manager-clients"></a>Klienci programu Configuration Manager
W przypadku urządzeń z systemem Windows 10, które są klientów programu Configuration Manager można zarejestrować te urządzenia i włączyć zarządzanie wspólnej z konsoli programu Configuration Manager. Wyzwalacze programu Configuration Manager, automatycznej rejestracji w usłudze Intune oparta na usłudze Azure AD dzierżawy informacji.  


## <a name="remote-actions-available-in-intune-on-azure-for-co-managed-devices"></a>Zdalne Akcje dostępne w usłudze Intune na platformie Azure dla wspólnie zarządzanych urządzeń
Po włączeniu urządzenia z systemem Windows 10 do zarządzania wspólnej masz następujące akcje zdalnego dostępne dla użytkownika z usługi Intune na platformie Azure:  
- [Resetowanie do ustawień fabrycznych](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
- [Selektywne czyszczenie danych](https://docs.microsoft.com/intune/apps-selective-wipe)
- [Usuwanie urządzeń](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
- [Ponowne uruchomienie urządzenia](https://docs.microsoft.com/intune/device-restart)
- [Nowa start](https://docs.microsoft.com/intune/device-fresh-start)

## <a name="next-steps"></a>Następne kroki
[Przygotowywanie urządzeń z systemem Windows 10 pod kątem współzarządzania](co-management-prepare.md)