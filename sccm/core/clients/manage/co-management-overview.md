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
ms.openlocfilehash: 3d7ca4bb72f6f3f76855faac125385374347ba55
ms.sourcegitcommit: d67c6246bb6027cd5501e772b0521f9272407c28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="co-management-for-windows-10-devices"></a>Jednoczesne zarządzania dla urządzeń z systemem Windows 10    
 Z poprzedniej aktualizacji systemu Windows 10, urządzenia z systemem Windows 10 można już Dołącz do lokalnej usługi Active Directory (AD) i oparta na chmurze usługi Azure AD, w tym samym czasie (rozwiązanie hybrydowe usługi Azure AD). Począwszy od programu Configuration Manager w wersji 1710 wspólnej zarządzania korzysta z tego ulepszenia i umożliwia jednocześnie zarządzanie urządzeniami 1709 wersji systemu Windows 10, używając programu Configuration Manager i usługi Intune. <!-- 1350871 -->
## <a name="why-co-management"></a>Dlaczego wspólnej zarządzania?
Wielu klientów chcesz zarządzać urządzeniami z systemem Windows 10 w taki sam sposób ich zarządzania urządzeniami przenośnymi za pomocą uproszczonego, ekonomiczne, oparte na chmurze rozwiązanie. Jednak przejścia z tradycyjnego zarządzania do zarządzania nowoczesnymi może być trudne.  
## <a name="what-is-co-management"></a>Co to jest wspólna management?
Zarządzanie wspólnej umożliwia jednocześnie zarządzać urządzeniami z systemem Windows 10, używając programu Configuration Manager i usługi Intune. To rozwiązanie, które zapewnia mostek z tradycyjnego zarządzania nowoczesnymi i umożliwia ścieżki do dokonania zmiany przy użyciu podejście etapowe.

## <a name="benefits"></a>Korzyści 
- Natychmiastowe korzystanie z funkcji usługi Intune 
    - Akcje zdalnych
        - [Resetowanie do ustawień fabrycznych](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
        - [Selektywne czyszczenie danych](https://docs.microsoft.com/intune/apps-selective-wipe)
        - [Usuwanie urządzeń](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
        - [Ponowne uruchomienie urządzenia](https://docs.microsoft.com/intune/device-restart)
        - [Nowa start](https://docs.microsoft.com/intune/device-fresh-start)
    - Orchestration przy użyciu usługi Intune dla następujących zadań:
        - [Zasady zgodności](https://docs.microsoft.com/intune/device-compliance-get-started)
        - [Zasady dostępu do zasobów](https://docs.microsoft.com/intune/device-profiles)
        - [Zasady usługi Windows Update](https://docs.microsoft.com/intune/windows-update-for-business-configure)
        - [Program Endpoint Protection](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10), rozpoczynając w 1802 Menedżera konfiguracji. <!-- 1357365 -->
    
## <a name="how-to-configure-co-management"></a>Konfigurowanie zarządzania wspólnej
Istnieją dwa główne ścieżki do wspólnego zarządzania. Jedna jest inicjowana zarządzania wspólnej gdzie przyłączone do urządzeń z systemem Windows 10 zarządzane przez program Configuration Manager i hybrydowe usługi Azure AD zarejestrować się w usłudze Intune w programie Configuration Manager. Druga to Intune zainicjowano obsługę administracyjną urządzeń, które są zarejestrowane w usłudze Intune, a następnie instalowany z zasięgu klienta programu Configuration Manager stanu zarządzania wspólnej.

### <a name="configuration-manager"></a>**Configuration Manager**
 -  Uaktualnienie do programu Configuration Manager w wersji 1710 lub nowszej.


### <a name="azure-active-directory"></a>**Usługa Azure Active Directory**
  - [Przyłączony do hybrydowej usługi Azure AD](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) (dołączony do usługi AD i Azure AD).
  - [Włączanie automatycznej rejestracji systemu Windows 10.](https://docs.microsoft.com/intune/windows-enroll)


### <a name="intune"></a>**Intune**
 - [Jak skonfigurować subskrypcję usługi Intune.](/sccm/mdm/deploy-use/configure-intune-subscription) lub https://docs.microsoft.com/en-us/intune/setup-steps
 - [Uruchom migrację z hybrydowego zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune.](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa)


### <a name="enable-co-management"></a>Włącz zarządzanie wspólnej 
 W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze**  >  **Zarządzania wspólnej**. Wybierz **konfigurowania zarządzania wspólnej** na Wstążce, aby otworzyć **Kreator przechodzenia do wspólnego zarządzania** 
   
1. Na **subskrypcji** kliknij przycisk **logowania** i zaloguj się do dzierżawy usługi Intune, a następnie kliknij przycisk **dalej**.    
2. W **włączenie** wybierz Twoje **automatycznej rejestracji w usłudze Intune** ustawienie. Wiersz polecenia dla urządzenia już zarejestrowane w usłudze Intune, należy skopiować, jeśli to konieczne. 
3. Na **obciążeń** strony dla poszczególnych obciążeń, wybierz grupę urządzeń, aby przenieść do zarządzania za pomocą usługi Intune.
4. W **przemieszczania** wybierz kolekcję urządzeń jako **pilotażowe kolekcji**. Sprawdź **Podsumowanie** i Zakończ pracę kreatora. 

### <a name="upgrade-windows-10-client"></a>Uaktualnij klienta systemu Windows 10
- Uaktualnij do [systemu Windows 10, wersja 1709 (znanej także jako aktualizacja twórców spadek) lub nowszy](/sccm/osd/deploy-use/manage-windows-as-a-service)

### <a name="configure-workloads-to-switch-to-intune"></a>Skonfiguruj obciążeń, aby przełączyć się do usługi Intune 
[Obciążenia mógł zostać przeniesieni do usługi Intune](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune) artykule przedstawiono sposób przełączyć konkretnych obciążeń programu Configuration Manager do usługi Intune. Artykuł zawiera również instrukcje dotyczące zmiany grup urządzeń, dla których są przenoszone obciążeń.

- **Zasady zgodności:** Zasady zgodności definiują reguły i ustawienia, które urządzenie musi spełniać, aby można je było uważać za spełniające zasady dostępu warunkowego. Zasady zgodności mogą być również wykorzystane do monitorowania i rozwiązywania problemów ze zgodnością urządzeń niezależnie od dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [zasady zgodności urządzeń](https://docs.microsoft.com/intune/device-compliance-get-started).  

- **Zasady usługi Windows Update:** Windows Update dla firm, zasady umożliwiają konfigurowanie zasad odroczenia aktualizacje funkcji systemu Windows 10 lub jakości aktualizacje dla urządzeń z systemem Windows 10 zarządzanych bezpośrednio przez usługę Windows Update dla firm. Aby uzyskać więcej informacji, zobacz [skonfigurować usługi Windows Update dla firm odroczenia zasad](https://docs.microsoft.com/intune/windows-update-for-business-configure).  

- **Zasady dostępu do zasobów:** Zasady dostępu do zasobów skonfigurować sieci VPN, Wi-Fi, poczty e-mail i ustawienia certyfikatów na urządzeniach. Aby uzyskać więcej informacji, zobacz [wdrażania profilów dostępu do zasobów](https://docs.microsoft.com/intune/device-profiles).

- **Program Program Endpoint Protection:** Począwszy od programu Configuration Manager 1802 obciążenia programu Endpoint Protection może zostać przeniesieni do usługi Intune. Aby uzyskać więcej informacji, zobacz [programu Endpoint Protection usługi Microsoft Intune](https://docs.microsoft.com/en-us/intune/endpoint-protection-windows-10) <!-- 1357365 --> i [obciążenia mógł zostać przeniesieni do usługi Intune](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune)


### <a name="install-configuration-manager-client-to-the-devices-enrolled-in-intune"></a>Zainstaluj klienta programu Configuration Manager na urządzeniach zarejestrowanych w usłudze Intune
W przypadku urządzeń z systemem Windows 10 zarejestrowanych w usłudze Intune, można zainstalować klienta programu Configuration Manager na urządzeniach ([przy użyciu określonego argumentu wiersza polecenia](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client)) do przygotowania klientów do wspólnego zarządzania. Następnie możesz włączyć zarządzanie wspólnej z konsoli programu Configuration Manager pomyśleć konkretnych obciążeń do usługi Intune dla konkretnych urządzeń z systemem Windows 10.
Dla urządzeń z systemem Windows 10, które nie zostały jeszcze zarejestrowane w usłudze Intune można użyć automatycznego rejestrowania na platformie Azure rejestracji urządzeń. W przypadku nowych urządzeń z systemem Windows 10, można użyć [Windows AutoPilot](https://docs.microsoft.com/intune/enrollment-autopilot) skonfigurować poza (tryb OOBE Box Experience), w tym automatycznego rejestrowania, który umożliwia rejestrację urządzeń w usłudze Intune.
 - Włącz [brama zarządzania chmury](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) w programie Configuration Manager (tylko w przypadku instalowania klienta programu Configuration Manager przy użyciu usługi Intune).

## <a name="monitor-co-management"></a>Monitorowania zarządzania wspólnej
[Pulpit nawigacyjny zarządzania wspólnej](/sccm/core/clients/manage/co-management-dashboard) pomaga Przejrzyj maszyny, które są zarządzane wspólnie w danym środowisku. Wykresy ułatwiają identyfikowanie urządzeń, które mogą wymagać uwagi.


## <a name="next-steps"></a>Następne kroki
[Przygotowywanie urządzeń z systemem Windows 10 pod kątem współzarządzania](co-management-prepare.md)
