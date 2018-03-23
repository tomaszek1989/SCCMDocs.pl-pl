---
title: Przygotowywanie urządzenia z systemem Windows 10 do zarządzania wspólnej
description: Dowiedz się, jak przygotować urządzenia z systemem Windows 10 do zarządzania wspólnej.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology: ''
ms.assetid: 101de2ba-9b4d-4890-b087-5d518a4aa624
ms.openlocfilehash: 61aef0351e32ef6cf31911a8dfd27e86de82f38c
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="prepare-windows-10-devices-for-co-management"></a>Przygotowywanie urządzenia z systemem Windows 10 do zarządzania wspólnej
Można włączyć wspólnej zarządzania na urządzeniach z systemem Windows 10, które są przyłączone do usługi AD i Azure AD i zarejestrowane w usłudze Intune i klienta w programie Configuration Manager. Dla nowych urządzeń z systemem Windows 10, a w przypadku urządzeń, które są już zarejestrowane w usłudze Intune należy zainstalować klienta programu Configuration Manager, zanim zostaną umieszczone zarządzanych. Dla urządzeń z systemem Windows 10, które są już klientów programu Configuration Manager możesz zarejestrować urządzenia w usłudze Intune i włączyć wspólnej zarządzanie w konsoli programu Configuration Manager.

> [!IMPORTANT]
> Urządzenia przenośne z systemem Windows 10 nie obsługują zarządzania wspólnej.

## <a name="command-line-to-install-configuration-manager-client"></a>Wiersz polecenia, aby zainstalować klienta programu Configuration Manager
Tworzenie aplikacji w usłudze Intune dla systemu Windows 10 urządzeń, które nie są już klientów programu Configuration Manager. Podczas tworzenia aplikacji w kolejnych sekcjach, należy użyć następującego polecenia:

ccmsetup.msi CCMSETUPCMD = "/ mp:&#60;*adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania*&#62;/ CCMHOSTNAME =&#60;*adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania* &#62;SMSSiteCode =&#60;*Kod_lokacji* &#62; SMSMP = https:&#47;/&#60;*FQDN MP* &#62; AADTENANTID =&#60;*Identyfikatora dzierżawy usługi AAD*  &#62; AADTENANTNAME =&#60;*nazwa_dzierżawcy* &#62; AADCLIENTAPPID =&#60;*AppID Server dla integracji usługi AAD* &#62; AADRESOURCEURI = https:&#47;/&#60;*identyfikator zasobu*&#62;"

Na przykład, jeśli masz następujące wartości:

- **Adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania**: https:/&#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    

   >[!Note]    
   >Użyj **MutualAuthPath** wartość w **vProxy_Roles** widoku SQL dla **adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania** wartość.

- **Nazwa FQDN punktu zarządzania (MP)**: sccmmp.corp.contoso.com    
- **Kod lokacji**: PS1    
- **Identyfikator dzierżawy usługi Azure AD**: 72F988BF-86F1-41AF-91AB-2D7CD011XXXX    
- **Nazwa dzierżawy usługi Azure AD**: contoso    
- **Identyfikator aplikacji klienta usługi Azure AD**: bef323b3-042f-41a6-907a-f9faf0d1XXXX     
- **Identyfikator URI identyfikator zasobu usługi AAD**: ConfigMgrServer    

  > [!Note]    
  > Użyj **IdentifierUri** wartość znajduje się w **vSMS_AAD_Application_Ex** widoku SQL dla **AAD zasobów identyfikator URI** wartość.

Należy użyć następującego polecenia:

ccmsetup.msi CCMSETUPCMD="/mp:https:/&#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode=PS1 SMSMP=https:/&#47;sccmmp.corp.contoso.com AADTENANTID=72F988BF-86F1-41AF-91AB-2D7CD011XXXX AADTENANTNAME=contoso  AADCLIENTAPPID=bef323b3-042f-41a6-907a-f9faf0d1XXXX AADRESOURCEURI=https:/&#47;ConfigMgrServer”

> [!Tip]
> Parametry wiersza polecenia można znaleźć w witrynie przy użyciu następujących kroków:     
> 1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze**  >  **Zarządzania wspólnej**.  
> 2. Na karcie Narzędzia główne w grupie zarządzania, wybierz **konfigurowania zarządzania wspólnej** aby otworzyć Kreator przechodzenia do wspólnego zarządzania.    
> 3. Na stronie subskrypcji kliknij **logowania** i zaloguj się do dzierżawy usługi Intune, a następnie kliknij przycisk **dalej**.    
> 4. Na stronie aktywacji kliknij **kopiowania** w **urządzeń zarejestrowanych w usłudze Intune** sekcji można skopiować do Schowka w wierszu polecenia, a następnie zapisz wiersza polecenia do użycia w procedurze do utworzenia aplikacji.  
> 5. Kliknij przycisk **anulować** aby zakończyć pracę kreatora.

> [!Important]    
> W przypadku dostosowania wiersza polecenia do zainstalowania klienta programu Configuration Manager, upewnij się, że wiersza polecenia nie może przekraczać 1024 znaków. W wierszu polecenia jest większa niż 1024 znaki, instalacja klienta nie powiedzie się.


## <a name="new-windows-10-devices"></a>Nowe urządzenia z systemem Windows 10
Dla nowych urządzeń z systemem Windows 10 Usługa Autopilot służy do konfigurowania poza pole środowisko, w tym przyłączania urządzenia do usługi AD i Azure AD, a także rejestrowanie urządzenia w usłudze Intune. Następnie utwórz aplikację w usłudze Intune do wdrażania klienta programu Configuration Manager.  
1. Włącz AutoPilot dla nowych urządzeń z systemem Windows 10. Aby uzyskać więcej informacji, zobacz [AutoPilot omówienie Windows](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot).    

   > [!NOTE]   
   > Począwszy od wersji 1802, użyj Menedżera konfiguracji umożliwia zbieranie i raportowanie informacji o urządzeniu wymagane przez Microsoft Store dla firm i Education. Informacje te obejmują numer seryjny urządzenia, identyfikator produktu systemu Windows i identyfikatora sprzętu. W konsoli programu Configuration Manager **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** węzła, rozwiń węzeł **raporty**i wybierz **sprzęt — ogólne**  węzła. Uruchom nowy raport **informacje o urządzeniu AutoPilot Windows** i wyświetlić wyniki. W podglądzie raportów kliknij **wyeksportować** ikonę, a następnie wybierz **CSV (rozdzielany przecinkami)** opcji. Po zapisaniu pliku, należy przekazać dane do Microsoft Store dla firm i Education. Aby uzyskać więcej informacji, zobacz [urządzenia można dodać na Microsoft Store dla firm i Education](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile).

2. Skonfigurowanie automatycznego rejestrowania w usłudze Azure AD dla urządzeń do automatycznej rejestracji w usłudze Intune. Aby uzyskać więcej informacji, zobacz [urządzeń Windows zarejestrować usługi Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).
3. Tworzenie aplikacji w usłudze Intune przy użyciu pakietu klienta programu Configuration Manager i wdrażanie aplikacji na urządzeniach Windows 10, które mają być zarządzane wspólnie. Użyj [wiersza polecenia do zainstalowania klienta programu Configuration Manager](#command-line-to-install-configuration-manager-client) po przejściu przez proces [instalowania klientów z Internetu przy użyciu usługi Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).   

## <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Urządzenia z systemem Windows 10 nie zostało zarejestrowane w usłudze Intune lub klienta programu Configuration Manager
Dla urządzeń z systemem Windows 10, które nie są zarejestrowane w usłudze Intune lub klienta programu Configuration Manager można użyć automatycznego rejestrowania, aby zarejestrować urządzenie w usłudze Intune. Następnie utwórz aplikację w usłudze Intune do wdrażania klienta programu Configuration Manager.
1. Skonfigurowanie automatycznego rejestrowania w usłudze Azure AD dla urządzeń do automatycznej rejestracji w usłudze Intune. Aby uzyskać więcej informacji, zobacz [urządzeń Windows zarejestrować usługi Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).  
2. Tworzenie aplikacji w usłudze Intune przy użyciu pakietu klienta programu Configuration Manager i wdrażanie aplikacji na urządzeniach Windows 10, które mają być zarządzane wspólnie. Użyj [wiersza polecenia do zainstalowania klienta programu Configuration Manager](#command-line-to-install-configuration-manager-client) po przejściu przez proces [instalowania klientów z Internetu przy użyciu usługi Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).

## <a name="windows-10-devices-enrolled-in-intune"></a>Urządzenia z systemem Windows 10 zarejestrowanych w usłudze Intune
Dla urządzeń z systemem Windows 10, które są już zarejestrowane w usłudze Intune należy utworzyć aplikację w usłudze Intune do wdrażania klienta programu Configuration Manager. Użyj [wiersza polecenia do zainstalowania klienta programu Configuration Manager](#command-line-to-install-configuration-manager-client) po przejściu przez proces [instalowania klientów z Internetu przy użyciu usługi Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).  

## <a name="next-steps"></a>Następne kroki
[Przełączanie obciążeń programu Configuration Manager do usługi Intune](co-management-switch-workloads.md)