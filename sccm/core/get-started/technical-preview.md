---
title: Technical Preview dla programu System Center Configuration Manager | Dokumentacja firmy Microsoft
description: "Informacje o wersji Technical Preview, że Załóżmy możesz test-drive nowych funkcji i możliwości w programie System Center Configuration Manager."
ms.custom: na
ms.date: 4/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 157
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 3a7370fedee417588d219dc7bff46205faf42929
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

**Zapraszamy do programu System Center Configuration Manager Technical Preview**. W tym temacie przedstawiono szczegółowe informacje na temat ewoluującej wersji zapoznawczej obejmującej nowe funkcje i możliwości, nad którymi pracujemy. Z każdą wersją technical preview wprowadzono nowe funkcje, które nie są uwzględnione w bieżącej gałęzi programu System Center Configuration Manager w momencie udostępnienia wersji technical preview. Te funkcje mogą zostać później dołączone w aktualizacji wersji Current Branch, ale zanim zostaną ukończone i dodane, chcemy aby mogły zostać wypróbowane przez użytkowników i uzyskać ich opinie.  

 Ponieważ ten temat dotyczy wersji zapoznawczej Technical Preview, szczegóły i funkcje mogą ulec zmianie.  

 Ten temat zawiera informacje, które mają zastosowanie do wszystkich wersji Technical Preview i zawiera także listę poszczególnych nowe możliwości (lub funkcji) wraz z wersji Technical Preview, w której możliwości najpierw pojawia się, jak wersja 1701 dla stycznia 2017. Szczegółowe informacje o tych możliwościach przedstawiono w oddzielnych tematach poświęconych poszczególnym wersjom zapoznawczym.  

 Aby uzyskać informacje na temat nowości w bieżącej gałęzi programu Configuration Manager, zobacz [nowości w programie System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Wymagania i ograniczenia wersji zapoznawczej Technical Preview  

> [!IMPORTANT]     
>  Wersja zapoznawcza Technical Preview jest licencjonowana tylko do użytku w środowisku laboratoryjnym.  Firma Microsoft może zatem nie świadczyć usług pomocy technicznej związanych z tą wersją, a określone funkcje mogą być niedostępne w wersji zapoznawczej oprogramowania. Ponadto oprogramowanie w wersji zapoznawczej może mieć ograniczone lub inne standardy zabezpieczeń, ochrony prywatności, ułatwień dostępu, dostępności i niezawodności w porównaniu z oprogramowaniem dostępnym w sprzedaży.  

 Dla większości produktu wymagania wstępne, skorzystaj z informacji w [obsługiwanych konfiguracji programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md). Do wersji zapoznawczych Technical Preview mają zastosowanie następujące wyjątki:  

-   Każda instalacja pozostaje aktywna przez 90 dni. Następnie staje się nieaktywna.  

-   Jedynym obsługiwanym językiem jest angielski.


-   Obsługiwane są tylko następujące flagi instalacji (przełączniki):  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Domyślnie gdy używasz technical preview, punkt połączenia usługi ustawiono do trybu online podczas instalacji, a nie obsługuje zmiany do trybu offline.

-   W razie konieczności dodatkowe ograniczenia i wymagania znajdują się w szczegółowych informacjach dotyczących określonej wersji zapoznawczej Technical Preview.  

-   Brak obsługi migracji do tej kompilacji w wersji zapoznawczej lub z niej.  

-   Brak obsługi uaktualniania do tej kompilacji w wersji zapoznawczej.  

-   Brak obsługi uaktualniania z kompilacji w wersji zapoznawczej do kompilacji produkcyjnej (Current Branch). Jednakże, gdy aktualizacje są dostępne w wersji preview, można znaleźć i zainstalować je z **aktualizacji i obsługi** węzeł konsoli programu Configuration Manager. Aby obejrzeć film wideo przedstawiający proces uaktualniania w konsoli, zobacz [Installing ConfigMgr Update Packages](https://www.youtube.com/embed/KBd_EGFbUT8) (Instalowanie pakietów aktualizacji programu Configuration Manager) w witrynie youtube.com.  
-   Obsługiwana jest tylko autonomiczna lokacja główna. Brak obsługi centralnej lokacji administracyjnej, wielu lokacji głównych i lokacji dodatkowych.  

Następujące produkty i technologie są obsługiwane przez tej gałęzi programu Configuration Manager. Jednak włączenie ich do tej zawartości nie oznacza rozszerzenie pomocy technicznej dla danego produktu lub wersji, która jest wyższy niż cyklu pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza ich zasady świadczenia pomocy technicznej nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji na temat cykli wsparcia technicznego firmy Microsoft, zobacz witrynę sieci Web [Cykl wsparcia technicznego produktów firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) .  

-   Obsługiwane są tylko następujące wersje programu SQL Server:  

    -   SQL Server 2016 (bez dodatku Service Pack i nowsze)
    -   SQL Server 2014 (z dodatkiem Service Pack 1 lub nowszym)
    -   SQL Server 2012 (z Service Pack 3 lub nowszym)


-   Lokacja obsługuje do 10 klientów, na których musi działać jeden z tych systemów operacyjnych:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> Instalowanie i aktualizowanie wersji zapoznawczej Technical Preview  
 System Center Configuration Manager Technical Preview różni się od bieżącej wersji programu System Center Configuration Manager.  

 Aby użyć wersji zapoznawczej Technical Preview, należy najpierw zainstalować **wersję bazową** kompilacji wersji zapoznawczej Technical Preview. Po zainstalowaniu wersji bazowej należy uaktualnić tę kompilację za pomocą **aktualizacji w konsoli** , aby upewnić się, że instalacja będzie zgodna z najnowszą wersją zapoznawczą.     Zazwyczaj nowe wersje Technical Preview są dostępne w każdym miesiącu.

Każda wersja zapoznawcza jest obsługiwana aż trzy kolejne wersje są dostępne. To znaczy, wydań wersji 1702, przestaną być wersji 1610 w pomocy technicznej, ale wersje 1611, 1612 i 1701 pozostać w pomocy technicznej. Planu bazowego wypada poza pomocy technicznej (na przykład wersja 1610), jest nadal obsługiwane instalowania nowej lokacji Technical Preview, dopóki nie jest dostępna nowa wersja linii bazowej tak długo, jak następnie zaktualizuj tę instalację do obsługiwanej wersji. Podczas aktualizacji, jeśli nie widzisz najnowszej wersji dostępnej w konsoli, aktualizacji do najnowszej wersji i następnie powtórz ten proces można zainstalować najnowszą wersję technical preview.

> [!TIP]  
>  Po zainstalowaniu aktualizacji wersji zapoznawczej Technical Preview należy zaktualizować instalację wersji wstępnej do nowej wersji zapoznawczej Technical Preview.    W przypadku instalacji wersji zapoznawczej Technical Preview nigdy nie ma możliwości uaktualnienia do instalacji Current Branch ani otrzymania aktualizacji z wersji Current Branch.  

**Aktywne wersje bazowe Technical Preview:**  
Można zainstalować wersję linii bazowej do 1 rok po jego wydaniu. Jednak po zainstalowaniu nowej lokacji technical preview, zaleca się, że używasz najnowszej wersji linii bazowej, które są dostępne.
-  **Technical Preview 1703** -Configuration Manager Technical Preview 1703 jest dostępna zarówno aktualizację w konsoli Configuration Manager Technical Preview, jak i nowa wersja linii bazowej, dostępnej w witrynie TechNet Centrum ewaluacji.

-  **Technical Preview 1610** -Configuration Manager Technical Preview 1610 było dostępne w obu aktualizacji w konsoli Configuration Manager Technical Preview, jak i wersji linii bazowej. Jeśli masz nośnik instalacji 1610, zaleca się pobrać wersję 1703 i opcję instalacji tej wersji.




##  <a name="BKMK_TPFeedback"></a> Przekazywanie opinii  
 Czekamy na Twoją opinię na temat wersji zapoznawczych Technical Preview. Aby przesłać opinię na temat funkcji poszczególnych wersji zapoznawczych, skorzystaj z linku do formularza opinii na stronie [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) w witrynie Microsoft Connect.  

 Czekamy też na pomysły dotyczące nowych funkcji. Aby przesłać nowe pomysły i zagłosować na pomysły innych osób, [odwiedź stronę z opiniami użytkowników naszego oprogramowania](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> Możliwości zapewniane przez wersje zapoznawcze Technical Preview  
 Dostępne są następujące możliwości dostarczane z każdej wersji technical preview programu Configuration Manager.  Możliwości, które są dostępne od wersji zapoznawczej Technical Preview, pozostają dostępne w kolejnych wersjach. Podobnie funkcje, które zostały dodane do wydania System Center Configuration Manager (bieżącej gałęzi) pozostają dostępne w kolejnych wersji zapoznawczych technicznych.  Kliknij informacje o poszczególnych wersjach zapoznawczych, aby uzyskać więcej informacji o określonej możliwości.  

 |Możliwość |Wersja zapoznawcza techniczne |Bieżąca wersja gałęzi|  
|----------------|---------------------|--------------------|
 |Konfigurowanie aplikacji systemu Android za pomocą zasad konfiguracji aplikacji  |[Podgląd tech 1704](capabilities-in-technical-preview-1704.md#configure-android-apps-with-app-configuration-policies)|![Nie dodano](media/Red_X.gif)|
 |Spis sprzętu zbiera informacje Bezpieczny rozruch |[Podgląd tech 1704](capabilities-in-technical-preview-1704.md#hardware-inventory-collects-secure-boot-information)|![Nie dodano](media/Red_X.gif)|
 |Dodaj sekwencji zadań podrzędnych do sekwencji zadań|[Podgląd tech 1704](capabilities-in-technical-preview-1704.md#add-child-task-sequences-to-a-task-sequence)|![Nie dodano](media/Red_X.gif)|
 |Załaduj ponownie obrazy rozruchowe z bieżącą wersję środowiska Windows PE |[Podgląd tech 1704](capabilities-in-technical-preview-1704.md#reload-boot-images-with-current-windows-pe-version)|![Nie dodano](media/Red_X.gif)|
 |Ulepszenia dotyczące wdrażania systemu operacyjnego|[Podgląd tech 1704](capabilities-in-technical-preview-1704.md#improvements-to-operating-system-deployment)|![Nie dodano](media/Red_X.gif)|
 |Wdrażanie aplikacji iOS kupionymi woluminu do kolekcji urządzeń|[Podgląd tech 1703](capabilities-in-technical-preview-1703.md#deploy-volume-purchased-ios-apps-to-device-collections)|[Wersja 1702](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)|
 |Łączy bezpośrednich do aplikacji w Centrum oprogramowania|[Podgląd tech 1703](capabilities-in-technical-preview-1703.md#direct-links-to-applications-in-software-center)|![Nie dodano](media/Red_X.gif)
 |Certyfikaty PFX dla komputerów klienckich programu Configuration Manager systemu Windows|[Podgląd tech 1703](capabilities-in-technical-preview-1703.md#pfx-certificates-for-configuration-manager-windows-client-computers)|![Nie dodano](media/Red_X.gif)|
 |Skonfiguruj kreatora usług Azure|[Podgląd tech 1703](capabilities-in-technical-preview-1703.md#configure-azure-services-wizard)|![Nie dodano](media/Red_X.gif)|
 |Konwersji z systemu BIOS z interfejsem UEFI w sekwencji zadań uaktualnienia systemu operacyjnego| [Podgląd tech 1703](capabilities-in-technical-preview-1703.md#convert-from-bios-to-uefi-during-an-in-place-upgrade) |[Wersja 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)|
 |Grupy sekwencji zadań zwijany| [Podgląd tech 1703](capabilities-in-technical-preview-1703.md#collapsible-task-sequence-groups) |![Nie dodano](media/Red_X.gif)|
 |Ustawienia klienta, aby skonfigurować module analiz systemu Windows pod kątem gotowości do uaktualnienia | [Podgląd tech 1703](capabilities-in-technical-preview-1703.md#client-settings-to-configure-windows-analytics-for-upgrade-readiness) |![Nie dodano](media/Red_X.gif)|
 |Nowe ustawienia zgodności dla urządzeń z systemem iOS|[Podgląd tech 1702](capabilities-in-technical-preview-1702.md#new-compliance-settings-for-ios-devices)|[Wersja 1702](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)|
 |Tworzenie certyfikatów PFX z obsługą S/MIME|[Podgląd tech 1702](capabilities-in-technical-preview-1702.md#create-pfx-certificates-with-s-mime-support)|[Wersja 1702](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Sprawdź, czy uruchomiony pliki wykonywalne przed zainstalowaniem aplikacji|[Podgląd tech 1702](capabilities-in-technical-preview-1702.md#check-for-running-executable-files-before-installing-an-application)|[Wersja 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Wyślij opinię z konsoli programu Configuration Manager | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#send-feedback-from-the-configuration-manager-console)    |[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#send-feedback-from-the-configuration-managercconsole)  |
 |Zmiany aktualizacji i obsługi  | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#changes-for-updates-and-servicing)  |[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#changes-for-updates-and-servicing) |
 |Ulepszenia pamięci podręcznej elementu równorzędnego  | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#peer-cache-improvements) |[Wersja 1702](/sccm/core/plan-design/hierarchy/client-peer-cache)|
 |Użyj usługi Azure Active Directory  | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |![Nie dodano](media/Red_X.gif)|
 |Ulepszenia zasady zgodności urządzeń dostępu warunkowego | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#conditional-access-device-compliance-policy-improvements) |[Wersja 1702](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Alert wersji klienta ochrony przed złośliwym oprogramowaniem | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert) |[Wersja 1702](/sccm/protect/deploy-use/endpoint-configure-alerts?branch=live#alert-for-outdated-malware-client)|
 |Oceny zgodności dla usługi Windows Update aktualizacje biznesowe | [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |![Nie dodano](media/Red_X.gif)|
 |Ulepszenia w ustawieniach Centrum oprogramowania i komunikatów powiadomień dla sekwencji zadań wysoki wpływ|[Podgląd tech 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert)|[Wersja 1702](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)|
 |Android obsługi pracy| [Podgląd tech 1702](capabilities-in-technical-preview-1702.md#android-for-work-support) |[Wersja 1702](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-for-work-enrollment)|
 |Punkty aktualizacji ulepszenia grup granic dla oprogramowania | [Podgląd tech 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |[Wersja 1702](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)  |
 |Spis sprzętu zbiera informacje z interfejsem UEFI | [Podgląd tech 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|[Wersja 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#hardware-inventory-collects-uefi-information) |
 |Ulepszenia dotyczące wdrażania systemu operacyjnego| [Podgląd tech 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment) |
 |Aktualizacje oprogramowania w punktach dystrybucji w chmurze| [Podgląd tech 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|![Nie dodano](media/Red_X.gif) |
 |Sprawdzanie poprawności danych zaświadczania kondycji urządzenia przy użyciu punktów zarządzania| [Podgląd tech 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)| [Wersja 1702](/sccm/core/servers/manage/health-attestation) |
 |Łącznik usługi OMS chmury Microsoft Azure Rząd |[Podgląd tech 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |[Wersja 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig) |
 |Android i iOS wersje nie są już targetable w kreatorach tworzenia |[Podgląd tech 1701](capabilities-in-technical-preview-1701.md#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |![Nie dodano](media/Red_X.gif) |
 |Dostęp do danych punktu końcowego OData |[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![Nie dodano](media/Red_X.gif)|
 |Punkt usługi magazynu danych |[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|[Wersja 1702](/sccm/core/servers/manage/data-warehouse)|
 |Narzędzie do oczyszczania biblioteki zawartości |[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|[Wersja 1702](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) |
 |Udoskonalenia w zakresie wyszukiwania w konsoli |[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-for-in-console-search)|
 |Zapobiec instalacji aplikacji, jeśli określony program jest uruchomiony|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|[Wersja 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Nowy Windows Hello Powiadomienia biznesowe dla użytkowników końcowych|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|![Nie dodano](media/Red_X.gif)|
 |Sklep Windows dla wsparcia biznesowego w programie Configuration Manager|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|![Nie dodano](media/Red_X.gif)|
 |Powrócić do poprzedniej strony, gdy sekwencja zadań zakończy się niepowodzeniem.|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment)|
 |Pliki instalacji ekspresowej obsługę aktualizacji systemu Windows 10|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|[Wersja 1702](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)|
 |Dołączanie do usługi Azure Active Directory|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|![Nie dodano](media/Red_X.gif)|
 |Zmień na konfigurowanie uwierzytelnianie wieloskładnikowe dla rejestracji urządzeń|[Podgląd tech 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![Nie dodano](media/Red_X.gif)|
 |Wstępnie buforowanie zawartości dla wdrożeń i sekwencji zadań |[Podgląd tech 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|[Wersja 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
 |Ustawienia konfiguracji usługi Windows Defender|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[Wersja 1610](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Żądanie zasad synchronizacji z konsoli administratora|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[Wersja 1610](/sccm/mdm/deploy-use/sync-intune-device)|
 |Dodatkowe zabezpieczenia roli obsługę wszystkich urządzeń należących do węzła|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[Wersja 1610](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Funkcja dostępu warunkowego dla profilów sieci VPN systemu Windows 10|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[Wersja 1610](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |Filtrowanie według rozmiaru zawartości w zasadach wdrażania automatycznego|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[Wersja 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |Udoskonalone funkcje w oknach dialogowych wymaganego oprogramowania|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[Wersja 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Odrzucanie żądań uprzednio zatwierdzonych aplikacji|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[Wersja 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Wyklucz klienci z automatycznej aktualizacji|[Podgląd tech 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[Wersja 1610](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Ulepszenia Endpoint Protection|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|[Wersja 1610](/sccm/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)|
 |Zwiększenie liczby zarejestrowanych urządzeń|[Podgląd tech 1609](/sccm/mdm/deploy-use/enable-platform-enrollment)|[Wersja 1610](/sccm/mdm/deploy-use/enable-platform-enrollment)|
 |Dodatkowe ustawienia DEP firmy Apple|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[Wersja 1610](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Rozszerzenia do Sklepu Windows biznesowych integracji z programem Configuration Manager|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md)|[Wersja 1610](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Nowe ustawienia zgodności dla elementów konfiguracji|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[Wersja 1610](/sccm/compliance/deploy-use/create-configuration-items)|
 |Integracja z analizy uaktualnienia|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[Wersja 1610](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |Profile VPN hybrydowe typy połączeń macierzystego for Windows 10|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![Nie dodano](media/Red_X.gif)|
 |Udoskonalenia w zakresie grup granic|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[Wersja 1610](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Pulpit nawigacyjny zarządzania klientami usługi Office 365|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[Wersja 1610](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |Wdrażanie aplikacji Office 365 na klientów|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|[Wersja 1702](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)|
 |Ulepszenia systemu BIOS z interfejsem UEFI konwersji|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[Wersja 1610](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Wykresy zgodności Intune|[Podgląd tech 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[Wersja 1610](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|
 |Ulepszenia kroku sekwencji zadań Przygotuj klienta programu ConfigMgr do przechwycenia|[Podgląd tech 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[Wersja 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |Ulepszenia programu Software Center|[Podgląd tech 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[Wersja 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Usprawnienia analizy zasobów|[Podgląd tech 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|![Nie dodano](media/Red_X.gif)|
 |Translacja klawiatury zdalnego sterowania|[Podgląd tech 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)|![Nie dodano](media/Red_X.gif)|
 |Ulepszenia zasad uaktualniania wersji systemu Windows 10|[Podgląd tech 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[Wersja 1610](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |Możliwość dostosowania znaków firmowych w oknach dialogowych Centrum oprogramowania|[Podgląd tech 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|![Nie dodano](media/Red_X.gif)|  
 |Wiele punktów zarządzania urządzeniami w ramach lokalnego zarządzania urządzeniami przenośnymi|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |Automatyczne kategoryzowanie urządzeń do kolekcji|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[Wersja 1606](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |Okres prolongaty wymuszania dla wdrożeń wymaganych aplikacji i aktualizacji oprogramowania|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[Wersja 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Korzystanie z programu Configuration Manager jako zarządzanego instalatora z funkcją ochrony urządzeń|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|![Nie dodano](media/Red_X.gif)|
 |Brama zarządzania chmury (wcześniej znane jako serwer Proxy usługi w chmurze)|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [Wersja 1610](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Zarządzanie agentem klienta usługi Office 365 w programie Configuration Manager|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |Zmienna sekwencji zadań OSDPreserveDriveLetter została uznana za przestarzałą|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[Wersja 1606](/sccm/osd/understand/task-sequence-built-in-variables) |
 |Zmiany dotyczące węzła Aktualizacje i obsługa|[Podgląd tech 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Sieć VPN dla aplikacji dla urządzeń z systemem Windows 10|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[Wersja 1606](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |Ulepszenia sekwencji zadań Zainstaluj aktualizacje oprogramowania|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |Ulepszenia kroku sekwencji zadań Przygotuj klienta programu ConfigMgr do przechwycenia |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[Wersja 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |Okres prolongaty dla wdrożeń wymaganych aplikacji |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|![Nie dodano](media/Red_X.gif)|  
 |Nowe środowisko dla akcji urządzeń zdalnych |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Aplikacje ze Sklepu Windows dla firm |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[Wersja 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Ogólne ulepszenia dotyczące aplikacji nabytych w ramach programu zakupów zbiorczych|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Ochrona danych w przedsiębiorstwie (EDP)|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Użytkownicy końcowi nie mogą instalować aplikacji z poziomu Portalu firmy |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|![Nie dodano](media/Red_X.gif)|  
 |Nowe karty aktualizacji i systemów operacyjnych w Centrum oprogramowania|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Obsługa grupy serwerów |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[Wersja 1606](/sccm/sum/deploy-use/service-a-server-group)|   
 |Obsługa usługi Zaawansowana ochrona przed zagrożeniami programu Windows Defender |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[Wersja 1606](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |Nowe opcje ponownego uruchamiania dla klientów z systemem Windows 10 po instalacji aktualizacji oprogramowania|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[Wersja 1606](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |Zaświadczanie o kondycji urządzenia lokalnego |[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[Wersja 1606](/sccm/core/servers/manage/health-attestation)|  
 |Wstępne deklarowanie urządzeń należących do przedsiębiorstwa przy użyciu numeru IMEI lub numeru seryjnego systemu iOS|[Podgląd tech 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[Wersja 1606](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  
 |Zarządzanie aplikacjami zakupionymi zbiorczo w Sklepie Windows dla firm| [Podgląd tech 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[Wersja 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Ulepszenia zarządzania w usłudze Microsoft Passport for Work|[Podgląd tech 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Opcja przełączania klientów do nowego punktu aktualizacji oprogramowania|[Podgląd tech 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[Wersja 1606](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |Ustawienia klienta do zarządzania ustawieniami pamięci podręcznej klienta i buforowania równorzędnego klienta |[Podgląd tech 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|Ustawienia klienta: [Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>Buforowanie równorzędne: [Wersja 1610](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |Obsługa usługi Passport for Work jako dostawcy magazynu kluczy |[Podgląd tech 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[Wersja 1606](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |Zaświadczanie o kondycji urządzenia lokalnego|[Podgląd tech 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[Wersja 1606](/sccm/core/servers/manage/health-attestation)|  
 |Ustawienie SmartLock dla urządzeń z systemem Android|[Podgląd tech 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[Wersja 1606](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 <!--  TP 1603 Aged out of support and all features in Current Branch Builds:
 |Improvements to Software Center|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Improvements to remote control|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
-->
 Jeśli wszystkie funkcje z wersji technical preview nie są dostępne w minimalna obsługiwana wersja bieżącej gałęzi, szczegóły dotyczące tej wersji zapoznawczej zostaną usunięte z tej tabeli.


## <a name="see-also"></a>Zobacz też  
[Nowości w programie System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md)

