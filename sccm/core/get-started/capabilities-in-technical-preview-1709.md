---
title: Technical Preview 1709
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1709 programu System Center Configuration Manager."
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3ef6bdc-a204-4c4c-a02f-2bd03f35183e
author: erikje
ms.author: erikje
manager: angrobe
ms.openlocfilehash: f0acc5ae0d8207dce92c56a4c80e8321faf51393
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1709-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1709 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1709. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Znane problemy w tej wersji Technical Preview:**
-   **Aktualizacja do wersji 1709 podglądu zakończy się niepowodzeniem, jeśli masz serwer lokacji w trybie pasywnym**. Po uruchomieniu wersji zapoznawczej 1706, 1707 lub 1708 i mieć [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), aby może pomyślnie zaktualizować lokację preview do wersji 1709 należy najpierw odinstalować serwer lokacji w trybie pasywnym. Po lokalizacji uruchomiono wersję 1709 można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku, kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="improved-vpn-profile-experience-in-configuration-manager-console"></a>Udoskonalone środowisko profil sieci VPN w konsoli programu Configuration Manager
<!-- 1313282 -->
W tej wersji Zaktualizowaliśmy VPN profilu Kreatora właściwości strony i aby wyświetlić ustawienia odpowiednie dla wybranej platformy. W szczególności:

- Dotyczy wszystkich platform własną przepływu pracy, co oznacza, że nowych profilów sieci VPN zawiera tylko ustawienia, które są obsługiwane przez platformę.
- **Obsługiwane platformy** zostaną wyświetlone po strony **ogólne** strony.  Możesz teraz wybrać platformę przed ustawieniem wartości właściwości.
- Gdy ma wartość platformy **Android**, **Android for Work**, lub **Windows Phone 8.1**, **obsługiwane platformy** strona nie jest wymagana i jest nie są wyświetlane.
- Przepływ pracy oparty na klienta programu Configuration Manager została połączona z hybrydowego urządzeniami przenośnymi (MDM) opartego na kliencie systemu Windows 10 przepływy pracy; obsługują one tych samych ustawień.
- Każda platforma przepływ pracy zawiera tylko ustawienia odpowiednie dla tego przepływu pracy.  Na przykład Android przepływ pracy zawiera ustawienia właściwe dla systemu Android; Ustawienia właściwe dla systemu iOS lub Windows 10 Mobile są już wyświetlane w przepływie pracy z systemem Android.
- Ustawienia zarządzane przez program Configuration Manager wyraźnie są oznaczone dla urządzeń Windows 8.1.
- Na stronie automatyczne połączenie VPN jest przestarzały i został usunięty.

Te zmiany dotyczą nowych profilów sieci VPN.  

Aby zminimalizować ryzyko zgodności, istniejących profilów sieci VPN nie uległy zmianie.  Podczas edycji istniejącego profilu, ustawienia, są tak samo, jak podczas tworzenia profilu.  

### <a name="try-it-out"></a>Wypróbuj

Utwórz nowy profil sieci VPN przy użyciu standardowego procesu. Zwróć uwagę, że zostały zmienione na pierwszej stronie Kreatora profilu sieci VPN opcje.

1.  Przejdź do **zasoby i zgodność** > **omówienie** > **ustawień zgodności** > **dostęp do zasobów firmy**   >  **Profilów sieci VPN** , a następnie wybierz **Tworzenie profilu sieci VPN**.
2.  Wprowadź nazwę **ogólne** strony i wybierz jedną z następujących opcji w obszarze **Określ typ profilu sieci VPN, aby utworzyć**:

    - Windows 10  
    - Windows 8.1  
    - Windows Phone 8,1  
    - iOS i macOS  
    - Android  
    - Android for Work  

3.  Jeśli wybierzesz **Windows 8.1**, masz możliwość **Utwórz nowy profil** lub **Import z pliku**.
4.  Ukończ pracę kreatora, aby zakończyć tworzenie profilu.

Po wybraniu różnych platform, zwróć uwagę, tylko ustawienia odpowiednie do wyświetlenia wybranej platformy.

## <a name="co-management-for-windows-10-devices"></a>Jednoczesne zarządzania dla urządzeń z systemem Windows 10    
<!-- 1350871 -->
Wielu klientów chcesz zarządzać urządzeniami z systemem Windows 10 w taki sam sposób ich zarządzania urządzeniami przenośnymi za pomocą uproszczonego, ekonomiczne, oparte na chmurze rozwiązanie. Jednak przejścia z tradycyjnego zarządzania do zarządzania nowoczesnymi może być trudne. Począwszy od systemu Windows 10 w wersji 1607 (znanej także jako aktualizacja rocznicy), można dołączyć urządzenie z systemem Windows 10 do lokalnej usługi Active Directory (AD) i oparta na chmurze usługi Azure AD, w tym samym czasie (rozwiązanie hybrydowe usługi Azure AD). Wspólnej zarządzania korzysta z tego ulepszenia i umożliwia jednocześnie zarządzać urządzeniami z systemem Windows 10, używając programu Configuration Manager i usługi Intune. To rozwiązanie, które zapewnia mostek z tradycyjnego zarządzania nowoczesnymi i umożliwia ścieżki do dokonania zmiany przy użyciu podejście etapowe. 

### <a name="prerequisites"></a>Wymagania wstępne
Musi mieć następujące wymagania wstępne w miejscu, aby można było włączyć zarządzania wspólnej. Istnieją ogólne wymagania wstępne i inne wymagania wstępne dla istniejących klientów programu Configuration Manager i urządzeń, które nie są klientami.

### <a name="known-issues"></a>Znane problemy
Po utworzeniu zasad zarządzania wspólnej nie można edytować zasady. Aby zmienić zasady, usuń go, a następnie utwórz ją ponownie przy użyciu ustawień, które są potrzebne. 

#### <a name="general-prerequisites"></a>Ogólne wymagania wstępne
Poniżej przedstawiono ogólne wymagania wstępne, aby włączyć zarządzanie wspólnej:  

- Technical Preview dla 1709 wersji programu Configuration Manager
- Usługi Azure AD 
- Licencji pakietu EMS lub usługi Intune dla wszystkich użytkowników
- Subskrypcję usługi Intune &#40; Ustaw urząd zarządzania urządzeniami Przenośnymi w usłudze Intune **Intune**&#41;

   > [!Note]  
   > Jeśli masz środowiska hybrydowego zarządzania urządzeniami Przenośnymi (usługa Intune zintegrowana z programem Configuration Manager), nie można włączyć zarządzania wspólnej. Jeśli interesuje Cię migracji do autonomicznej usługi Intune, zobacz [rozpocząć migrację z hybrydowego zarządzania urządzeniami Przenośnymi do autonomicznej usługi Intune](/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).

#### <a name="additional-prerequisites-for-existing-configuration-manager-clients"></a>Dodatkowe wymagania wstępne dla istniejących klientów programu Configuration Manager
- Windows 10, wersja 1709 (spadek twórców aktualizacji) lub nowszy
- Hybrydowe usługi Azure AD przyłączony (dołączone do usługi AD i Azure AD)

#### <a name="additional-prerequisites-for-new-windows-10-devices"></a>Dodatkowe wymagania wstępne dotyczące nowych urządzeń z systemem Windows 10
- Windows 10, wersja 1709 (spadek twórców aktualizacji) lub nowszy
- [Brama zarządzania w chmurze](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) w programie Configuration Manager

### <a name="workloads-you-can-switch-to-intune"></a>Obciążenia można przełączyć się do usługi Intune
Po włączeniu wspólnego zarządzania programu Configuration Manager nadal zarządza wszystkich obciążeń. W przypadku podjęcia decyzji, że wszystko będzie gotowe, program może rozpocząć zarządzanie obciążeń dostępności usługi Intune. W tej wersji może mieć następujące obciążenia zarządzania usługi Intune.   

#### <a name="compliance-policies"></a>Zasady zgodności
Zasady zgodności definiują reguły i ustawienia, które urządzenie musi spełniać, aby można je było uważać za spełniające zasady dostępu warunkowego. Zasady zgodności mogą być również wykorzystane do monitorowania i rozwiązywania problemów ze zgodnością urządzeń niezależnie od dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [zasady zgodności urządzeń](https://docs.microsoft.com/en-us/sccm/mdm/deploy-use/device-compliance-policies).  

#### <a name="windows-update-for-business-policies"></a>Usługi Windows Update dla firm zasad
Windows Update dla firm, zasady umożliwiają konfigurowanie zasad odroczenia aktualizacje funkcji systemu Windows 10 lub jakości aktualizacje dla urządzeń z systemem Windows 10 zarządzanych bezpośrednio przez usługę Windows Update dla firm. Aby uzyskać więcej informacji, zobacz [skonfigurować usługi Windows Update dla firm odroczenia zasad](https://docs.microsoft.com/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies).  

### <a name="remote-actions-available-in-intune-on-azure-for-co-managed-devices"></a>Zdalne Akcje dostępne w usłudze Intune na platformie Azure dla wspólnie zarządzanych urządzeń
Po włączeniu urządzenia z systemem Windows 10 do zarządzania wspólnej masz następujące akcje zdalnego dostępne dla użytkownika z usługi Intune na platformie Azure:  
- [Resetowanie do ustawień fabrycznych](https://docs.microsoft.com/intune/devices-wipe#factory-reset)
- [Selektywne czyszczenie danych](https://docs.microsoft.com/intune/apps-selective-wipe)
- [Usuwanie urządzeń](https://docs.microsoft.com/intune/devices-wipe#delete-devices-from-the-azure-active-directory-portal)
- [Ponowne uruchomienie urządzenia](https://docs.microsoft.com/intune/device-restart)
- [Nowa start](https://docs.microsoft.com/intune/device-fresh-start)

### <a name="prepare-intune-for-co-management"></a>Przygotowanie usługi Intune do zarządzania wspólnej
Przed przejściem obciążeń z programu Configuration Manager do usługi Intune, tworzenie profilów i zasad, które są potrzebne w usłudze Intune do zapewnienia, że urządzenia mają być chronione.
Można tworzyć obiektów w usłudze Intune oparte na obiektach, które mają w programie Configuration Manager. Lub, jeśli bieżący strategii jest oparta na starszej wersji lub tradycyjnego zarządzania, warto Zabierz krok do rozważenie jakie zasad i profilów potrzebne do zarządzania nowoczesnymi. Użyj następujących zasobów do tworzenia zasad i profilów.    
<!-- - [Device compliance policies](https://docs.microsoft.com/intune/compliance-policy-create-windows)  -->
- [Usługi Windows Update dla firm zasad](https://docs.microsoft.com/intune/windows-update-for-business-configure)  
- [Profilów konfiguracji urządzeń](https://docs.microsoft.com/intune/device-profile-create)  

### <a name="architectural-overview-for-co-management"></a>Omówienie architektury zarządzania wspólnej
Następujący diagram zawiera omówienie architektury wspólnego zarządzania i jego miejsce w istniejącej infrastruktury konfiguracji i usługi Intune.

![Diagram architektury zarządzania wspólnej](./media/co-management-arch-cm1709tp.svg)

### <a name="scenarios-to-enable-co-management"></a>Scenariusze umożliwiające zarządzanie wspólnej  
Umożliwiają jednoczesne zarządzanie zarówno na urządzeniach z systemem Windows 10 zarejestrowanych w programie Microsoft Intune i istniejących klientów systemu Windows 10 Configuration Manager. Oba scenariusze spowodować urządzeń z systemem Windows 10 jednocześnie zarządzane przez program Configuration Manager i usługi Intune, jak również do usługi AD i Azure AD.  

#### <a name="devices-enrolled-in-intune"></a>Urządzenia zarejestrowane w usłudze Intune  
W przypadku urządzeń z systemem Windows 10 zarejestrowanych w usłudze Intune, aby przygotować klientów do wspólnego zarządzania można zainstalować klienta programu Configuration Manager na urządzeniach (przy użyciu określonego argumentu wiersza polecenia). Następnie możesz włączyć zarządzanie wspólnej z konsoli programu Configuration Manager pomyśleć konkretnych obciążeń do usługi Intune dla konkretnych urządzeń z systemem Windows 10.  

Dla urządzeń z systemem Windows 10, które nie zostały jeszcze zarejestrowane w usłudze Intune można użyć automatycznego rejestrowania na platformie Azure rejestracji urządzeń. Dla nowych urządzeń z systemem Windows 10 Windows AutoPilot służy do konfigurowania poza (tryb OOBE Box Experience), w tym automatycznego rejestrowania, który umożliwia rejestrację urządzeń w usłudze Intune.  

#### <a name="configuration-manager-clients"></a>Klienci programu Configuration Manager
W przypadku urządzeń z systemem Windows 10, które są klientów programu Configuration Manager można zarejestrować te urządzenia i włączyć zarządzanie wspólnej z konsoli programu Configuration Manager. Wyzwalacze programu Configuration Manager, automatycznej rejestracji w usłudze Intune oparta na usłudze Azure AD dzierżawy informacji.  

### <a name="prepare-windows-10-devices-for-co-management"></a>Przygotowywanie urządzenia z systemem Windows 10 do zarządzania wspólnej
Można włączyć wspólnej zarządzania na urządzeniach z systemem Windows 10, które są przyłączone do usługi AD i Azure AD i zarejestrowane w usłudze Intune i klienta w programie Configuration Manager. Dla nowych urządzeń z systemem Windows 10, a w przypadku urządzeń, które są już zarejestrowane w usłudze Intune należy zainstalować klienta programu Configuration Manager, zanim zostaną umieszczone zarządzanych. Dla urządzeń z systemem Windows 10, które są już klientów programu Configuration Manager możesz zarejestrować urządzenia w usłudze Intune i włączyć wspólnej zarządzanie w konsoli programu Configuration Manager.

#### <a name="command-line-to-install-configuration-manager-client"></a>Wiersz polecenia, aby zainstalować klienta programu Configuration Manager
Tworzenie aplikacji w usłudze Intune dla systemu Windows 10 urządzeń, które nie są już klientów programu Configuration Manager. Podczas tworzenia aplikacji w kolejnych sekcjach, należy użyć następującego polecenia:

ccmsetup.msi CCMSETUPCMD = "/ mp: &#60; *Adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania*&#62; / CCMHOSTNAME = &#60; *Adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania*&#62; SMSSiteCode = &#60; *Kod_lokacji*&#62; SMSMP = https: &#47; / &#60; *FQDN punktu zarządzania*&#62; AADTENANTID = &#60; *Identyfikatora dzierżawy usługi AAD*&#62; AADTENANTNAME = &#60; *Nazwa dzierżawcy*&#62; AADCLIENTAPPID = &#60; *AppID server dla integracji usługi AAD*&#62; AADRESOURCEURI = https: &#47; / &#60; *Identyfikator zasobu*&#62; "

Na przykład, jeśli masz następujące wartości:

- **Adres URL punktu końcowego w chmurze zarządzania bramy wzajemnego uwierzytelniania**: https:/ &#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100    

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

ccmsetup.msi CCMSETUPCMD = "/ mp:https: / &#47;contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 CCMHOSTNAME=contoso.cloudapp.net/CCM_Proxy_MutualAuth/72057594037928100 SMSSiteCode = PS1 SMSMP = https: / &#47; sccmmp.corp.contoso.com AADTENANTID = AADTENANTNAME 72F988BF-86F1-41AF-91AB-2D7CD011XXXX = contoso AADCLIENTAPPID = AADRESOURCEURI bef323b3-042f-41a6-907a-f9faf0d1XXXX = https: / &#47; ConfigMgrServer"

> [!Tip]
>Parametry wiersza polecenia można znaleźć w witrynie przy użyciu następujących kroków:     
> 1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze**  >  **Zarządzania wspólnej**.  
> 2. Na karcie Narzędzia główne w grupie zarządzania, wybierz **konfigurowania zarządzania wspólnej** aby otworzyć Kreator przechodzenia do wspólnego zarządzania.    
> 3. Na stronie subskrypcji kliknij **logowania** i zaloguj się do dzierżawy usługi Intune, a następnie kliknij przycisk **dalej**.    
> 4. Na stronie aktywacji kliknij **kopiowania** w **urządzeń zarejestrowanych w usłudze Intune** sekcji można skopiować do Schowka w wierszu polecenia, a następnie zapisz wiersza polecenia do użycia w procedurze do utworzenia aplikacji.  
> 5. Kliknij przycisk **anulować** aby zakończyć pracę kreatora.

#### <a name="new-windows-10-devices"></a>Nowe urządzenia z systemem Windows 10
Dla nowych urządzeń z systemem Windows 10 Usługa Autopilot służy do konfigurowania poza pole środowisko, w tym przyłączania urządzenia do usługi AD i Azure AD, a także rejestrowanie urządzenia w usłudze Intune. Następnie utwórz aplikację w usłudze Intune do wdrażania klienta programu Configuration Manager.  
1. Włącz AutoPilot dla nowych urządzeń z systemem Windows 10. Aby uzyskać więcej informacji, zobacz [AutoPilot omówienie Windows](https://docs.microsoft.com/windows/deployment/windows-10-auto-pilot).  
2. Skonfigurowanie automatycznego rejestrowania w usłudze Azure AD dla urządzeń do automatycznej rejestracji w usłudze Intune. Aby uzyskać więcej informacji, zobacz [urządzeń Windows zarejestrować usługi Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).
3. Tworzenie aplikacji w usłudze Intune przy użyciu pakietu klienta programu Configuration Manager i wdrażanie aplikacji na urządzeniach Windows 10, które mają być zarządzane wspólnie. Użyj [wiersza polecenia do zainstalowania klienta programu Configuration Manager](#command-line-to-install-configuration-manager-client) po przejściu przez proces [instalowania klientów z Internetu przy użyciu usługi Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).   

#### <a name="windows-10-devices-not-enrolled-in-intune-or-a-configuration-manager-client"></a>Urządzenia z systemem Windows 10 nie zostało zarejestrowane w usłudze Intune lub klienta programu Configuration Manager
Dla urządzeń z systemem Windows 10, które nie są zarejestrowane w usłudze Intune lub klienta programu Configuration Manager można użyć automatycznego rejestrowania, aby zarejestrować urządzenie w usłudze Intune. Następnie utwórz aplikację w usłudze Intune do wdrażania klienta programu Configuration Manager.
1. Skonfigurowanie automatycznego rejestrowania w usłudze Azure AD dla urządzeń do automatycznej rejestracji w usłudze Intune. Aby uzyskać więcej informacji, zobacz [urządzeń Windows zarejestrować usługi Microsoft Intune](https://docs.microsoft.com/intune/windows-enroll).  
2. Tworzenie aplikacji w usłudze Intune przy użyciu pakietu klienta programu Configuration Manager i wdrażanie aplikacji na urządzeniach Windows 10, które mają być zarządzane wspólnie. Użyj [wiersza polecenia do zainstalowania klienta programu Configuration Manager](#command-line-to-install-configuration-manager-client) po przejściu przez proces [instalowania klientów z Internetu przy użyciu usługi Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).

#### <a name="windows-10-devices-enrolled-in-intune"></a>Urządzenia z systemem Windows 10 zarejestrowanych w usłudze Intune
Dla urządzeń z systemem Windows 10, które są już zarejestrowane w usłudze Intune należy utworzyć aplikację w usłudze Intune do wdrażania klienta programu Configuration Manager. Użyj [wiersza polecenia do zainstalowania klienta programu Configuration Manager](#command-line-to-install-configuration-manager-client) po przejściu przez proces [instalowania klientów z Internetu przy użyciu usługi Azure AD](https://docs.microsoft.com/en-us/sccm/core/clients/deploy/deploy-clients-cmg-azure).  

### <a name="switch-configuration-manager-workloads-to-intune"></a>Przełącz obciążeń programu Configuration Manager do usługi Intune
W poprzedniej sekcji przygotowywania urządzenia z systemem Windows 10 do zarządzania wspólnej. Te urządzenia są przyłączone do usługi AD i Azure AD i są zarejestrowane w usłudze Intune i zainstalować klienta Configuration Manager. Prawdopodobnie nadal masz urządzenia z systemem Windows 10, które dołączyły do usługi AD i klienta programu Configuration Manager, ale nie zostały dołączone do usługi Azure AD lub zarejestrowane w usłudze Intune. Poniższa procedura zawiera kroki, aby włączyć zarządzanie wspólnej przygotowanie pozostałe urządzenia z systemem Windows 10 (klientów programu Configuration Manager bez rejestracji w usłudze Intune) do wspólnego zarządzania i umożliwia rozpoczęcie przełączania określonego programu Configuration Manager obciążeń do usługi Intune.

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze**  >  **Zarządzania wspólnej**.    
2. Na karcie Narzędzia główne w grupie zarządzania, wybierz **konfigurowania zarządzania wspólnej** aby otworzyć Kreator przechodzenia do wspólnego zarządzania.    
3. Na stronie subskrypcji kliknij **logowania** i zaloguj się do dzierżawy usługi Intune, a następnie kliknij przycisk **dalej**.   
4. Na stronie przemieszczania, skonfiguruj następujące ustawienia, a następnie kliknij przycisk **dalej**:
    - **Grupy pilotażowej**: Grupy pilotażowej zawiera co najmniej jednej kolekcji, które można wybrać. Użyj tej grupy w ramach wdrożenia etapowego zarządzania wspólnej. Można rozpoczynać się od małej testowej kolekcji, a następnie dodaj więcej kolekcji, do grupy pilotażowe wdrożenie zarządzania wspólnej do większej liczby użytkowników i urządzeń. Kolekcje w grupie pilotażowego można zmienić w dowolnym momencie we właściwościach zarządzania wspólnej.
    - **Produkcji**: Po wybraniu tego ustawienia Wszystkie obsługiwane urządzenia z systemem Windows 10 są włączone do wspólnego zarządzania. Skonfiguruj **grupie wykluczenia** z co najmniej jedną kolekcję. Urządzenia, które są członkami kolekcji w tej grupie są wykluczone z za pomocą zarządzania wspólnej. 
5. Na stronie aktywacji wybierz **pilotażu** lub **wszystkie** (w zależności od ustawienia skonfigurowane na stronie przemieszczania) Włączanie automatycznej rejestracji w usłudze Intune, a następnie kliknij przycisk **dalej**. Po wybraniu **pilotażu**, tylko klienci programu Configuration manager, które są elementami członkowskimi grupy pilotażu automatycznie zarejestrowane w usłudze Intune. Dzięki temu można włączyć zarządzanie wspólnej w podzestawie klientów do początkowego testowania wspólnego zarządzania i zarządzania wspólnej wdrożenia przy użyciu podejście etapowe. 
6. Na stronie obciążeń wybierz, czy przełączyć obciążeń programu Configuration Manager mają być zarządzane przez usługę Intune, a następnie kliknij przycisk **dalej**. Za pomocą suwaków wybierz, czy przełączyć obciążenia do grupy pilotażu lub dla wszystkich klientów systemu Windows 10 (w zależności od ustawienia, które można skonfigurować na stronie przemieszczania). 
7. Aby włączyć zarządzanie wspólnej, Zakończ pracę kreatora.  

<!--### Modify your co-management settings
After you enable co-management using the wizard, you can modify your target group and change the workloads that are managed by Configuration Manager and Intune.  
- In the Configuration Manager console, go to **Administration** > **Overview** > **Cloud Services** > **Co-management**.  
Select the co-management object, and then on the Home tab, click **Properties**. -->   

<!--### Monitor co-management
After you have enabled co-management, you can monitor which devices are managed by Configuration Manager and which are managed by Intune. You can also see which Configuration Manager workloads are managed by which product.-->

## <a name="see-also"></a>Zobacz także
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview). 
