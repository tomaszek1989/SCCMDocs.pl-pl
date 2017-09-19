---
title: Technical Preview programu Configuration Manager | Dokumentacja firmy Microsoft
description: "Więcej informacji o wersji Technical Preview że teraz musisz test-drive nowe funkcje i możliwości w programie System Center Configuration Manager."
ms.custom: na
ms.date: 08/25/2017
ms.prod: configuration-manager
ms.reviewer: nab
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: "157"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: e471e11b3c61172b4e9fcae74944d39aa0ab702f
ms.sourcegitcommit: 31c670a4bce74fd64a7d46ebf7702f65b80d4147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2017
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

**Zapraszamy do programu System Center Configuration Manager Technical Preview**. W tym temacie przedstawiono szczegółowe informacje na temat ewoluującej wersji zapoznawczej obejmującej nowe funkcje i możliwości, nad którymi pracujemy. Przez poszczególne wersje technical Preview wprowadzono nowe funkcje, które nie znajdują się w bieżącej gałęzi programu System Center Configuration Manager w momencie udostępnienia wersji zapoznawczej technical preview. Te funkcje mogą zostać później dołączone w aktualizacji wersji Current Branch, ale zanim zostaną ukończone i dodane, chcemy aby mogły zostać wypróbowane przez użytkowników i uzyskać ich opinie.  

 Ponieważ ten temat dotyczy wersji zapoznawczej Technical Preview, szczegóły i funkcje mogą ulec zmianie.  

 Ten temat zawiera informacje dotyczą wszystkich wersji Technical Preview, a także zawiera listę poszczególnych nowej możliwości (lub funkcji) wraz z wersji zapoznawczej Technical Preview, w której możliwości najpierw pojawia się, jak wersja 1701 stycznia 2017 r. Szczegółowe informacje o tych możliwościach przedstawiono w oddzielnych tematach poświęconych poszczególnym wersjom zapoznawczym.  

 Aby uzyskać informacje na temat nowości w wersji current branch programu Configuration Manager, zobacz [nowości w programie System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Wymagania i ograniczenia wersji zapoznawczej Technical Preview  

> [!IMPORTANT]     
>  Wersja zapoznawcza Technical Preview jest licencjonowana tylko do użytku w środowisku laboratoryjnym.  Firma Microsoft może zatem nie świadczyć usług pomocy technicznej związanych z tą wersją, a określone funkcje mogą być niedostępne w wersji zapoznawczej oprogramowania. Ponadto oprogramowanie w wersji zapoznawczej może mieć ograniczone lub inne standardy zabezpieczeń, ochrony prywatności, ułatwień dostępu, dostępności i niezawodności w porównaniu z oprogramowaniem dostępnym w sprzedaży.  

 Dla większości wymagań wstępnych dotyczących produktów, skorzystaj z informacji w [obsługiwane konfiguracje programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md). Do wersji zapoznawczych Technical Preview mają zastosowanie następujące wyjątki:  

-   Każda instalacja pozostaje aktywna przez 90 dni. Następnie staje się nieaktywna.  

-   Jedynym obsługiwanym językiem jest angielski.


-   Obsługiwane są tylko następujące flagi instalacji (przełączniki):  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Korzystając z wersji technical preview punkt połączenia usługi jest domyślnie do trybu online podczas instalacji, a nie obsługuje zmiany do trybu offline.

-   W razie konieczności dodatkowe ograniczenia i wymagania znajdują się w szczegółowych informacjach dotyczących określonej wersji zapoznawczej Technical Preview.  

-   Brak obsługi migracji do tej kompilacji w wersji zapoznawczej lub z niej.  

-   Brak obsługi uaktualniania do tej kompilacji w wersji zapoznawczej.  

-   Brak obsługi uaktualniania z kompilacji w wersji zapoznawczej do kompilacji produkcyjnej (Current Branch). Jednak gdy aktualizacje są dostępne w wersji zapoznawczej, można znaleźć i zainstalować je z **aktualizacje i obsługa** węzła konsoli programu Configuration Manager. Aby obejrzeć film wideo przedstawiający proces uaktualniania w konsoli, zobacz [Installing ConfigMgr Update Packages](https://www.youtube.com/embed/KBd_EGFbUT8) (Instalowanie pakietów aktualizacji programu Configuration Manager) w witrynie youtube.com.  
-   Obsługiwana jest tylko autonomiczna lokacja główna. Brak obsługi centralnej lokacji administracyjnej, wielu lokacji głównych i lokacji dodatkowych.  

Następujące produkty i technologie, są obsługiwane przez gałęzi programu Configuration Manager. Jednak włączenie ich do tej zawartości nie oznacza to rozszerzenia obsługi dla produktu lub wersji, która wykracza poza cykl pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza wsparcia technicznego, nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji na temat cykli wsparcia technicznego firmy Microsoft, zobacz witrynę sieci Web [Cykl wsparcia technicznego produktów firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) .  

-   Obsługiwane są tylko następujące wersje programu SQL Server:  

    -   SQL Server 2016 (bez dodatku Service Pack i nowsze)
    -   SQL Server 2014 (z dodatkiem Service Pack 1 lub nowszy)
    -   SQL Server 2012 (bez dodatku Service Pack 3 lub nowszej)


-   Lokacja obsługuje do 10 klientów, na których musi działać jeden z tych systemów operacyjnych:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> Instalowanie i aktualizowanie wersji zapoznawczej Technical Preview  
 Programu System Center Configuration Manager Technical Preview różni się od bieżącej wersji programu System Center Configuration Manager.  

 Aby użyć wersji zapoznawczej Technical Preview, należy najpierw zainstalować **wersję bazową** kompilacji wersji zapoznawczej Technical Preview. Po zainstalowaniu wersji bazowej należy uaktualnić tę kompilację za pomocą **aktualizacji w konsoli** , aby upewnić się, że instalacja będzie zgodna z najnowszą wersją zapoznawczą.     Zazwyczaj nowe wersje Technical Preview są dostępne w każdym miesiącu.

Każdej wersji zapoznawczej jest obsługiwany, dopóki dostępne są trzy kolejne wersje. To znaczy, w wersjach 1708, wersja 1704 nie będzie go w obsłudze, ale wersje 1705, 1706 i 1707 pozostanie w obsłudze. Linii bazowej przypada poza pomocy technicznej (takie jak wersja 1703), jest nadal obsługiwane instalowania nowej lokacji Technical Preview, aż do nowej wersji linii bazowej jest dostępna, pod warunkiem, następnie zaktualizuj tę instalację do obsługiwanej wersji. Podczas aktualizacji, jeśli nie widzisz najnowszej wersji dostępnej w konsoli aktualizacji do najnowszej wersji i następnie powtórzyć ten proces, przed zainstalowaniem najnowszej wersji technical preview.

> [!TIP]  
>  Po zainstalowaniu aktualizacji wersji zapoznawczej Technical Preview należy zaktualizować instalację wersji wstępnej do nowej wersji zapoznawczej Technical Preview.    W przypadku instalacji wersji zapoznawczej Technical Preview nigdy nie ma możliwości uaktualnienia do instalacji Current Branch ani otrzymania aktualizacji z wersji Current Branch.  

**Aktywne wersje bazowe Technical Preview:**  
Można zainstalować wersji linii bazowej dla maksymalnie 1 rok po ich wydaniu. Jednak podczas instalowania nowej lokacji wersji zapoznawczej technical preview, firma Microsoft zaleca się, że używasz najnowszej wersji linii bazowej, która jest dostępna.
-  **Technical Preview 1703** — Configuration Manager Technical Preview 1703 jest dostępna jako zarówno aktualizacja w konsoli programu Configuration Manager Technical Preview, jak i nowa wersja bazowa jest [dostępne w witrynie TechNet Evaluation Center](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview).

<!-- out of support. Use baseline 1703
-  **Technical Preview 1610** - The Configuration Manager Technical Preview 1610 was available as both an in-console update for the Configuration Manager Technical Preview, and as a baseline version. If you have media for installing 1610, we recommend you download version 1703 and install that version instead.
-->



##  <a name="BKMK_TPFeedback"></a> Przekazywanie opinii  
 Czekamy na Twoją opinię na temat wersji zapoznawczych Technical Preview. Aby przesłać opinię na temat funkcji poszczególnych wersji zapoznawczych, skorzystaj z linku do formularza opinii na stronie [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) w witrynie Microsoft Connect.  

 Czekamy też na pomysły dotyczące nowych funkcji. Aby przesłać nowe pomysły i zagłosować na pomysły innych osób, [odwiedź stronę z opiniami użytkowników naszego oprogramowania](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a>Możliwości oferowane przez najnowszej wersji zapoznawczej technical preview  
 Poniżej przedstawiono możliwości oferowane w poszczególnych wersjach technical preview programu Configuration Manager.  Możliwości, które są dostępne od wersji zapoznawczej Technical Preview, pozostają dostępne w kolejnych wersjach. Podobnie możliwości, które zostały dodane do wersji System Center programu Configuration Manager (wersji current branch) pozostają dostępne w kolejnych wersjach technical Preview.  Kliknij informacje o poszczególnych wersjach zapoznawczych, aby uzyskać więcej informacji o określonej możliwości.  

 |Możliwość |Wersji Technical Preview |Bieżącą wersję gałęzi|  
 |----------------|---------------------|--------------------|
 |Ulepszenia określając Parametry skryptu, podczas wdrażania skryptów programu PowerShell z programu Configuration Manager<!-- 1236459 -->|[Podgląd techniczna 1708](capabilities-in-technical-preview-1708.md#improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)|![Nie dodano](media/Red_X.gif)|
 |Informacje na temat technologii zarządzania<!-- 1353967 --> |[Podgląd techniczna 1708](capabilities-in-technical-preview-1708.md#management-insights)|![Nie dodano](media/Red_X.gif)|
 |Uruchom ponownie komputer za pomocą konsoli programu Configuration Manager<!-- 1356283 --> |[Podgląd techniczna 1708](capabilities-in-technical-preview-1708.md#restart-computers-from-the-configuration-manager-console)|![Nie dodano](media/Red_X.gif)|
 |Dostosowywanie Centrum oprogramowania<!-- 1351224 --> |[Podgląd techniczna 1708](capabilities-in-technical-preview-1708.md#software-center-customization)|![Nie dodano](media/Red_X.gif)|


## <a name="capabilities-delivered-in-previous-technical-previews"></a>Możliwości oferowane w poprzednich wersjach technical Preview
 Gdy wszystkie funkcje z wersji technical preview są dostępne w minimalna obsługiwana wersja Current Branch, szczegóły dotyczące tej wersji zapoznawczej są usuwane z poniższej tabeli.  

 |Możliwość |Wersji Technical Preview |Bieżącą wersję gałęzi|  
 |----------------|---------------------|--------------------|
 |Klient równorzędnej pamięci podręcznej obsługę plików instalacji ekspresowej dla systemu Windows 10 i usługi Office 365|[Podgląd techniczna 1707](capabilities-in-technical-preview-1707.md#client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365)|![Nie dodano](media/Red_X.gif)|
 |Powierzchni urządzenia pulpitu nawigacyjnego|[Podgląd techniczna 1707](capabilities-in-technical-preview-1707.md#surface-device-dashboard)|![Nie dodano](media/Red_X.gif)|
 |Konfigurowanie i wdrażanie zasad Guard aplikacji programu Windows Defender|[Podgląd techniczna 1707](capabilities-in-technical-preview-1707.md#configure-and-deploy-windows-defender-application-guard-policies)|![Nie dodano](media/Red_X.gif)|
 |Dodawanie parametrów podczas wdrażania skryptów programu PowerShell z programu Configuration Manager|[Podgląd techniczna 1707](capabilities-in-technical-preview-1707.md#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager)|![Nie dodano](media/Red_X.gif)|
 |Nowe ustawienia zasad zarządzania aplikacjami mobilnymi|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#new-mobile-application-management-policy-settings)|![Nie dodano](media/Red_X.gif)|
 |Grupy granic ulepszone dla punktów aktualizacji oprogramowania|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#improved-boundary-groups-for-software-update-points)|[Wersja 1706](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)|
 |Wysoką dostępność roli serwera lokacji|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |![Nie dodano](media/Red_X.gif)|
 |Obejmują zaufania dla określonych plików i folderów w zasadach ochrony urządzeń|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#include-trust-for-specific-files-and-folders-in-a-device-guard-policy)|[Wersja 1706](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|
 |Ukryj postęp sekwencji zadań|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#hide-task-sequence-progress)|![Nie dodano](media/Red_X.gif)|
 |Określ inną lokalizację zawartości dla zawartości instalacji i odinstalowywania zawartości|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#specify-a-different-content-location-for-install-content-and-uninstall-content)|[Wersja 1706](/sccm/core/get-started/capabilities-in-technical-preview-1706#hide-task-sequence-progress)|
 |Ulepszenia ułatwień dostępu |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#accessibility-improvements)|[Wersja 1706](/sccm/core/understand/accessibility-features)|
 |Pomocy technicznej platformy Azure Kreator usług pod kątem gotowości do uaktualnienia |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#changes-to-the-azure-services-wizard-to-support-upgrade-readiness)|[Wersja 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Nowe ustawienia klienta dla usługi w chmurze|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#new-client-settings-for-cloud-services)|[Wersja 1706](/sccm/core/clients/deploy/deploy-clients-cmg-azure)|
 |Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#create-and-run-powershell-scripts-from-the-configuration-manager-console)|[Wersja 1706](/sccm/apps/deploy-use/create-deploy-scripts)|
 |Obsługa rozruchu środowiska PXE sieci IPv6 |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|![Nie dodano](media/Red_X.gif)|
 |Zarządzanie aktualizacjami sterownik Microsoft Surface |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#manage-microsoft-surface-driver-updates)|[Wersja 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#manage-microsoft-surface-driver-updates)|
 |Konfigurowanie usługi Windows Update dla zasad wykluczenia biznesowych |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#configure-windows-update-for-business-deferral-policies)|[Wersja 1706](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies)|
 |Ograniczenia rejestracji systemu iOS|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#android-and-ios-enrollment-restrictions)|[Wersja 1706](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac#configure-enrollment-restrictions)|
 |Ograniczenia rejestracja systemu android|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#android-and-ios-enrollment-restrictions)|[Wersja 1706](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)|
 |Android pracy zasad zarządzania aplikacjami do kopiowania i wklejania|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#android-for-work-application-management-policy-for-copy-paste)|[Wersja 1706](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client#android-for-work-configuration-item-settings-reference)|
 |Nowe ustawienia elementu konfiguracji systemu Windows|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#new-windows-configuration-item-settings)|[Wersja 1706](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Nowe reguły zasad zgodności urządzenia|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#new-device-compliance-policy-rules)|[Wersja 1706](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Ocena zaświadczania o kondycji urządzenia dla zasady zgodności dla dostępu warunkowego|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#device-health-attestation-assessment-for-compliance-policies-for-conditional-access)|![Nie dodano](media/Red_X.gif)|
 |Obsługa Entrust urzędów certyfikacji|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#support-for-entrust-certification-authorities)|[Wersja 1706](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Obsługa Cisco (IPSec) macOS profilów sieci VPN|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#cisco-ipsec-support-for-macos-vpn-profiles)|[Wersja 1706](/sccm/protect/deploy-use/vpn-profiles)|
 |Nowe możliwości dla usługi Azure AD i zarządzania w chmurze|[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#new-capabilities-for-azure-ad-and-cloud-management)|[Wersja 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#azure-ad-integration-with-configuration-manager)|
 |Konfigurowanie i wdrażanie zasad Guard aplikacji programu Windows Defender|[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#configure-and-deploy-windows-defender-application-guard-policies)|![Nie dodano](media/Red_X.gif)|
 |Narzędzie resetowania aktualizacji  |[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#update-reset-tool)|[Wersja 1706](/sccm/core/servers/manage/update-reset-tool)|
 |Obsługa konsoli usługi wysokiej rozdzielczości  |[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#high-dpi-console-support)|[Wersja 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#high-dpi-console-support)|
 |Ulepszenia pamięci podręcznej elementów równorzędnych  |[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#peer-cache-improvements) |[Wersja 1706](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache)|
 |Ulepszenia dla programu SQL Server, zawsze włączone grupy dostępności |[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#improvements-for-sql-server-always-on-availability-groups) |[Wersja 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#improvements-for-sql-server-always-on-availability-groups)|
 |Ulepszone powiadomienia użytkowników aktualizacji usługi Office 365|[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#improved-user-notifications-for-office-365-updates) |[Wersja 1706](/sccm/sum/deploy-use/manage-office-365-proplus-updates#restart-behavior-and-client-notifications-for-office-365-updates)|
 |Użyj kreatora usług Azure, aby skonfigurować połączenie z usługą OMS|[Podgląd techniczna 1705](capabilities-in-technical-preview-1705.md#use-azure-services-wizard-to-configure-a-connection-to-oms) |[Wersja 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Konfigurowanie aplikacji systemu Android przy użyciu zasad konfiguracji aplikacji  |[Podgląd techniczna 1704](capabilities-in-technical-preview-1704.md#configure-android-apps-with-app-configuration-policies)|![Nie dodano](media/Red_X.gif)|
 |Spisu sprzętu zbiera informacje Bezpieczny rozruch |[Podgląd techniczna 1704](capabilities-in-technical-preview-1704.md#hardware-inventory-collects-secure-boot-information)|[Wersja 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#hardware-inventory-collects-secure-boot-information)|
 |Dodaj do sekwencji zadań sekwencje zadań podrzędnych|[Podgląd techniczna 1704](capabilities-in-technical-preview-1704.md#add-child-task-sequences-to-a-task-sequence)|![Nie dodano](media/Red_X.gif)|
 |Załaduj ponownie obrazy rozruchowe z bieżącej wersji systemu Windows PE |[Podgląd techniczna 1704](capabilities-in-technical-preview-1704.md#reload-boot-images-with-current-windows-pe-version)|[Wersja 1706](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image)|
 |Ulepszenia dotyczące wdrażania systemu operacyjnego<!-- This item does not track to be added to the Current Branch. It is covered by various other incremental work. --> |[Podgląd techniczna 1704](capabilities-in-technical-preview-1704.md#improvements-to-operating-system-deployment)|![Nie dodano](media/Red_X.gif)|
 |Wdrażanie aplikacji dla systemu iOS zakupionymi zbiorczo do kolekcji urządzeń|[Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#deploy-volume-purchased-ios-apps-to-device-collections)|[Wersja 1702](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps)|
 |Linki bezpośrednie do aplikacji w programie Software Center|[Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#direct-links-to-applications-in-software-center)|[Wersja 1706](/sccm/apps/deploy-use/share-applications)
 |Certyfikaty PFX dla komputerów klienckich programu Configuration Manager systemu Windows|[Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#pfx-certificates-for-configuration-manager-windows-client-computers)|[Wersja 1706](/sccm/protect/deploy-use/create-certificate-profiles)|
 |Konfiguracja usług Azure — Kreator|[Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#configure-azure-services-wizard)|[Wersja 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Konwertowanie systemu BIOS na UEFI w sekwencji zadań uaktualniania systemu operacyjnego| [Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#convert-from-bios-to-uefi-during-an-in-place-upgrade) |[Wersja 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade)|
 |Grupy sekwencji zadań zwijanej| [Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#collapsible-task-sequence-groups) |[Wersja 1706](/sccm/core/plan-design/changes/whats-new-in-version-1706#collapsible-task-sequence-groups)|
 |Ustawienia klienta, aby skonfigurować module analiz systemu Windows pod kątem gotowości do uaktualnienia | [Podgląd techniczna 1703](capabilities-in-technical-preview-1703.md#client-settings-to-configure-windows-analytics-for-upgrade-readiness) |[Wersja 1706](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics)|
 |Nowe ustawienia zgodności dla urządzeń z systemem iOS|[Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#new-compliance-settings-for-ios-devices)|[Wersja 1702](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client)|
 |Tworzenie certyfikatów PFX z obsługą standardu S/MIME|[Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#create-pfx-certificates-with-s-mime-support)|[Wersja 1706](/sccm/mdm/deploy-use/create-pfx-certificate-profiles)|
 |Sprawdź, czy uruchamianie plików wykonywalnych przed zainstalowaniem aplikacji|[Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#check-for-running-executable-files-before-installing-an-application)|[Wersja 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Wyślij opinię z konsoli programu Configuration Manager | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#send-feedback-from-the-configuration-manager-console)    |[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#send-feedback-from-the-configuration-managercconsole)  |
 |Zmiany dotyczące aktualizacji i obsługi  | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#changes-for-updates-and-servicing)  |[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#changes-for-updates-and-servicing) |
 |Ulepszenia pamięci podręcznej elementów równorzędnych  | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#peer-cache-improvements) |[Wersja 1702](/sccm/core/plan-design/hierarchy/client-peer-cache)|
 |Użyj usługi Azure Active Directory<!-- This item does not track to be added to the Current Branch. It is covered by various other incremental work. --> | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |![Nie dodano](media/Red_X.gif)|
 |Ulepszenia zasad zgodności urządzenia dostępu warunkowego | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#conditional-access-device-compliance-policy-improvements) |[Wersja 1702](/sccm/mdm/deploy-use/create-compliance-policy)|
 |Alert wersji klienta ochrony przed złośliwym oprogramowaniem | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert) |[Wersja 1702](/sccm/protect/deploy-use/endpoint-configure-alerts?branch=live#alert-for-outdated-malware-client)|
 |Oceny zgodności dla usługi Windows Update dla firm aktualizacji | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |![Nie dodano](media/Red_X.gif)|
 |Ulepszenia w ustawieniach Centrum oprogramowania i komunikaty powiadomień dla sekwencji zadań o dużym wpływie na działanie|[Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#antimalware-client-version-alert)|[Wersja 1702](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)|
 |Android obsługę pracy| [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#android-for-work-support) |[Wersja 1702](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-for-work-enrollment)|
 |Punkty aktualizacji ulepszenia grup granic dla oprogramowania | [Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#boundary-groups-improvements-for-software-update-points)    |[Wersja 1702](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points)  |
 |Spisu sprzętu zbiera informacje z interfejsem UEFI | [Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#hardware-inventory-collects-uefi-information)|[Wersja 1702](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#hardware-inventory-collects-uefi-information) |
 |Ulepszenia dotyczące wdrażania systemu operacyjnego| [Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#improvements-to-operating-system-deployment)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment) |
 |Aktualizacje oprogramowania w punktach dystrybucji w chmurze| [Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#host-software-updates-on-cloud-based-distribution-points)|[Wersja 1702](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#plan-to-use-a-cloud-based-distribution-point) |
 |Sprawdzanie poprawności danych zaświadczania o kondycji urządzenia za pośrednictwem punktów zarządzania| [Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#validate-device-health-attestation-data-via-management-points)| [Wersja 1702](/sccm/core/servers/manage/health-attestation) |
 |Łącznik OMS chmury Microsoft Azure dla instytucji rządowych |[Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#use-the-oms-connector-for-microsoft-azure-government-cloud) |[Wersja 1702](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig) |
 |Wersje systemów android i iOS nie są już targetable w kreatorach tworzenia |[Podgląd techniczna 1701](capabilities-in-technical-preview-1701.md#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm) |
 |Dostęp do danych punktu końcowego OData |[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|![Nie dodano](media/Red_X.gif)|
 |Punkt usługi magazynu danych |[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#the-data-warehouse-service-point)|[Wersja 1702](/sccm/core/servers/manage/data-warehouse)|
 |Narzędzia do oczyszczania biblioteki zawartości |[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#content-library-cleanup-tool)|[Wersja 1702](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) |
 |Ulepszenia wyszukiwania w konsoli |[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#improvements-for-in-console-search)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-for-in-console-search)|
 |Zapobiegaj instalacji aplikacji, jeśli działa określonego programu|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#prevent-installation-of-an-application-if-a-specified-program-is-running)|[Wersja 1702](/sccm/apps/deploy-use/deploy-applications)|
 |Nowe usługi Windows Hello dla firm powiadomienia dla użytkowników końcowych|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#new-windows-hello-for-business-notification-for-end-users)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#new-windows-hello-for-business-notification-for-end-users)|
 |Sklep Windows dla firm pomocy technicznej w programie Configuration Manager|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#windows-store-for-business-support-in-configuration-manager)|[Wersja 1702](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Powrót do poprzedniej strony, gdy sekwencja zadań nie powiodło się.|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#return-to-previous-page-when-a-task-sequence-fails)|[Wersja 1702](/sccm/core/plan-design/changes/whats-new-in-version-1702#operating-system-deployment)|
 |Obsługa aktualizacji systemu Windows 10 pliki instalacji ekspresowej|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#express-installation-files-support-for-windows-10-updates)|[Wersja 1702](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates)|
 |Azure Active Directory dołączania|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#azure-active-directory-onboarding)|[Wersja 1706](/sccm/core/servers/deploy/configure/azure-services-wizard)|
 |Zmień na konfigurowanie uwierzytelniania wieloskładnikowego dla rejestracji urządzeń|[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#change-to-configuring-multi-factor-authentication-for-device-enrollment)|![Nie dodano](media/Red_X.gif)|
 |Wstępne wypełnienie pamięci podręcznej dla wdrożeń i sekwencji zadań |[Podgląd techniczna 1611](capabilities-in-technical-preview-1611.md#pre-cache-content-for-available-deployments-and-task-sequences)|[Wersja 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
 |Ustawienia konfiguracji usługi Windows Defender|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#windows-defender-configuration-settings)|[Wersja 1610](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client)|
 |Żądania zasady synchronizacji z konsoli administratora|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#request-policy-sync-from-administrator-console)|[Wersja 1610](/sccm/mdm/deploy-use/sync-intune-device)|
 |Obsługa roli dodatkowe zabezpieczenia dla węzła wszystkich firmowych urządzeń|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#additional-security-role-support)|[Wersja 1610](/sccm/mdm/understand/whats-new-in-hybrid-mobile-device-management#new-hybrid-features-in-november-2016)|
 |Dostęp warunkowy dla profilów sieci VPN systemu Windows 10|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#conditional-access-for-windows-10-vpn-profiles)|[Wersja 1610](/sccm/protect/deploy-use/create-vpn-profiles#configure-the-authentication-method-for-the-vpn-profile)|
 |Filtruj według rozmiaru zawartości w regułach wdrażania automatycznego|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#filter-by-content-size-in-automatic-deployment-rules)|[Wersja 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#filter-by-content-size-in-automatic-deployment-rules) |
 |Udoskonalone funkcje w oknach dialogowych wymaganego oprogramowania|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#improved-functionality-for-required-software-dialogs)|[Wersja 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Odrzucanie żądań zatwierdzone wcześniej aplikacji|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#deny-previously-approved-application-requests)|[Wersja 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Wyklucz z automatycznego uaktualnienia klientów|[Podgląd techniczna 1610](capabilities-in-technical-preview-1610.md#exclude-clients-from-automatic-upgrade)|[Wersja 1610](/sccm/core/clients/manage/upgrade/exclude-clients-windows)|
 |Ulepszenia dotyczące programu Endpoint Protection|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#improvements-to-endpoint-protection)|[Wersja 1610](/sccm/protect/deploy-use/endpoint-antimalware-policies#cloud-protection-service)|
 |Zwiększenie liczby zarejestrowanych urządzeń|[Podgląd techniczna 1609](/sccm/mdm/deploy-use/enable-platform-enrollment)|[Wersja 1610](/sccm/mdm/deploy-use/enable-platform-enrollment)|
 |Dodatkowe ustawienia programu DEP firmy Apple|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#additional-apple-dep-settings)|[Wersja 1610](/sccm/mdm/deploy-use/ios-device-enrollment-program-for-hybrid)|
 |Rozszerzenia do Sklepu Windows dla firm integracji z programem Configuration Manager|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md)|[Wersja 1610](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|
 |Nowe ustawienia zgodności dla elementów konfiguracji|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#new-compliance-settings-for-configuration-items)|[Wersja 1610](/sccm/compliance/deploy-use/create-configuration-items)|
 |Integracja z uaktualnienia analityka|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#integration-with-upgrade-analytics)|[Wersja 1610](/sccm/core/clients/manage/upgrade/upgrade-analytics)|
 |Profile sieci VPN hybrydowego typy połączeń natywnej dla systemu Windows 10|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#native-connection-types-for-windows-10-vpn-hybrid-profiles)|![Nie dodano](media/Red_X.gif)|
 |Ulepszenia grup granic|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#improvements-for-boundary-groups)|[Wersja 1610](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#BKMK_BoundaryGroups)|
 |Pulpit nawigacyjny zarządzania klienta usługi Office 365|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#office-365-client-management-dashboard)|[Wersja 1610](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard)|
 |Wdrażanie aplikacji usługi Office 365 na klientach|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#deploy-office-365-apps-to-clients)|[Wersja 1702](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps)|
 |Ulepszenia systemu BIOS z interfejsem UEFI konwersji|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#BKMK_UEFIConversion)|[Wersja 1610](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion)|
 |Wykresy zgodności usługi Intune|[Podgląd techniczna 1609](capabilities-in-technical-preview-1609.md#intune-compliance-charts)|[Wersja 1610](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)|
 |Ulepszenia kroku sekwencji zadań Przygotuj klienta programu ConfigMgr do przechwycenia|[Podgląd techniczna 1608](capabilities-in-technical-preview-1608.md#improvements-to-the-prepare-configmgr-client-for-capture-task-sequence-step)|[Wersja 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture)|
 |Ulepszenia Centrum oprogramowania|[Podgląd techniczna 1608](capabilities-in-technical-preview-1608.md#improvements-to-software-center)|[Wersja 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#general-improvements-to-software-center)|
 |Ulepszenia dotyczące analizy zasobów<!-- Listed as TBD. No planned addition to Current Branch -->|[Podgląd techniczna 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|![Nie dodano](media/Red_X.gif)|
 |Translacja klawiatury zdalnego sterowania|[Podgląd techniczna 1608](capabilities-in-technical-preview-1608.md#remote-control-keyboard-translation)| [Wersja 1610](/sccm/core/clients/manage/remote-control/configuring-remote-control#enable-keyboard-translation)|
 |Ulepszenia zasad uaktualniania wersji systemu Windows 10|[Podgląd techniczna 1607](capabilities-in-technical-preview-1607.md#dmp_edition)|[Wersja 1610](/sccm/compliance/deploy-use/upgrade-windows-version)|
 |Możliwość dostosowania znaków firmowych w oknach dialogowych Centrum oprogramowania|[Podgląd techniczna 1607](capabilities-in-technical-preview-1607.md#customizable-branding-for-software-center-dialogs)|[Wersja 1610](/sccm/core/plan-design/changes/whats-new-in-version-1610#customizable-branding-for-software-center-dialogs)|  
 |Wiele punktów zarządzania urządzeniami w ramach lokalnego zarządzania urządzeniami przenośnymi|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#dmp_onprem)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#on-premises-mobile-device-management)|
 |Automatyczne kategoryzowanie urządzeń do kolekcji|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#dmp_category)|[Wersja 1606](/sccm/core/clients/manage/collections/automatically-categorize-devices-into-collections) |
 |Okres prolongaty wymuszania dla wdrożeń wymaganych aplikacji i aktualizacji oprogramowania|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#dmp_grace)|[Wersja 1610](/sccm/apps/deploy-use/deploy-applications)|
 |Korzystanie z programu Configuration Manager jako zarządzanego instalatora z funkcją ochrony urządzeń|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#dmp_devg)|[Wersja 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager )|
 |Brama zarządzania chmury (dawniej serwera Proxy usługi w chmurze)|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#cloud_proxy) | [Wersja 1610](/sccm/core/clients/manage/plan-cloud-management-gateway)|  
 |Zarządzanie agentem klienta usługi Office 365 w programie Configuration Manager|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#manage_o365) |[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#software-updates)|  
 |Zmienna sekwencji zadań OSDPreserveDriveLetter została uznana za przestarzałą|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#osdpreservedriveletter) |[Wersja 1606](/sccm/osd/understand/task-sequence-built-in-variables) |
 |Zmiany dotyczące węzła Aktualizacje i obsługa|[Podgląd techniczna 1606](capabilities-in-technical-preview-1606.md#updatesandservicing)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#updates-and-servicing) |
 |Sieć VPN dla aplikacji dla urządzeń z systemem Windows 10|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_PerAppVPN)|[Wersja 1606](/sccm/protect/deploy-use/create-vpn-profiles)|  
 |Ulepszenia sekwencji zadań Zainstaluj aktualizacje oprogramowania|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_InstallSU)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
 |Ulepszenia kroku sekwencji zadań Przygotuj klienta programu ConfigMgr do przechwycenia |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_PrepareConfigMgrClient)|[Wersja 1610](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture) |
 |Okres prolongaty dla wdrożeń wymaganych aplikacji |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_Grace)|![Nie dodano](media/Red_X.gif)|  
 |Nowe środowisko dla akcji urządzeń zdalnych |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_Remote)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Aplikacje ze Sklepu Windows dla firm |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_WSFB)|[Wersja 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Ogólne ulepszenia dotyczące aplikacji nabytych w ramach programu zakupów zbiorczych|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP2)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Ochrona danych w przedsiębiorstwie (EDP)|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_VPP)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606)|  
 |Użytkownicy końcowi nie mogą instalować aplikacji z poziomu Portalu firmy |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|![Nie dodano](media/Red_X.gif)|  
 |Nowe karty aktualizacji i systemów operacyjnych w Centrum oprogramowania|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_SW1)|[Wersja 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Obsługa grupy serwerów |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|[Wersja 1606](/sccm/sum/deploy-use/service-a-server-group)|   
 |Obsługa usługi Zaawansowana ochrona przed zagrożeniami programu Windows Defender |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_ATP)|[Wersja 1606](/sccm/protect/deploy-use/windows-defender-advanced-threat-protection)|  
 |Nowe opcje ponownego uruchamiania dla klientów z systemem Windows 10 po instalacji aktualizacji oprogramowania|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_RestartOptions)|[Wersja 1606](/sccm/sum/plan-design/plan-for-software-updates#restart-options-for-Windows-10-clients-after-software-update-installation)|  
 |Zaświadczanie o kondycji urządzenia lokalnego |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_DHA)|[Wersja 1606](/sccm/core/servers/manage/health-attestation)|  
 |Wstępne deklarowanie urządzeń należących do przedsiębiorstwa przy użyciu numeru IMEI lub numeru seryjnego systemu iOS|[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_IMEI)|[Wersja 1606](/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id)|  

 <!--  TP 1604 and earlier has aged out of support and all features are in Current Branch builds:
 |Manage volume-purchased apps from the Windows Store for Business| [Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_WindowsVPP)|[Version 1606](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)|  
 |Improvements to Microsoft Passport for Work management|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_PFW)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#device-configuration-and-protection)|  
 |Option for clients to switch to a new software update point|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_switchsup)|[Version 1606](/sccm/sum/plan-design/plan-for-software-updates#BKMK_ManuallySwitchSUPs)|  
 |Client settings to manage Client Cache Settings and client Peer Cache |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_peercache)|Client Settings: [Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#administration)<br/>Peer Cache: [Version 1610](/sccm/core/plan-design/hierarchy/client-peer-cache)|  
 |Support for Passport for Work as a KSP |[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_passport)|[Version 1606](/sccm/protect/deploy-use/create-certificate-profiles)|  
 |On-premises Device Health Attestation|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#bkmk_onpremdha)|[Version 1606](/sccm/core/servers/manage/health-attestation)|  
 |SmartLock setting for Android devices|[Tech Preview 1604](capabilities-in-technical-preview-1604.md#BKMK_Smart)|[Version 1606](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-and-samsung-knox-configuration-item-settings-reference)|  
 |Improvements to Software Center|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_SC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#application-management)|  
 |Improvements to remote control|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RC1603)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#remote-control)|  
 |Customize the RamDisk TFTP block size and window size on PXE-enabled distribution points|[Tech Preview 1603](capabilities-in-technical-preview-1603.md#BKMK_RamDiskTFTP)|[Version 1606](/sccm/core/plan-design/changes/whats-new-in-version-1606#operating-system-deployment)|  
-->



## <a name="see-also"></a>Zobacz też  
[Co to jest nowe w programie System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md)
