---
title: Wersje Technical Preview
titleSuffix: Configuration Manager
description: Informacje o wersji Technical Preview, aby test-drive nowe funkcje i możliwości w programie Configuration Manager.
ms.date: 04/25/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: 157
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 79a535bd9ee7f597e551c2d4f84c39c84ecf262f
ms.sourcegitcommit: d67c6246bb6027cd5501e772b0521f9272407c28
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

**Zapraszamy do programu System Center Configuration Manager Technical Preview**. Ten artykuł zawiera szczegółowe informacje na temat ewoluującej wersji zapoznawczej, które wprowadza nowe funkcje i możliwości, które firma Microsoft pracuje nad. Każdej wersji technical Preview wprowadzono nowe funkcje, które nie znajdują się w bieżącej gałęzi programu Configuration Manager w momencie udostępnienia wersji zapoznawczej technical preview. Te funkcje mogą zostać później dołączone w aktualizacji wersji Current Branch, ale zanim zostaną ukończone i dodane, chcemy aby mogły zostać wypróbowane przez użytkowników i uzyskać ich opinie.  

 Ponieważ ta wersja jest technical preview, szczegóły i funkcje mogą ulec zmianie.  

 Ten artykuł zawiera informacje, które dotyczą wszystkich wersji Technical Preview. Każda nowa możliwość (lub funkcji) również wyświetlane wraz z wersji zapoznawczej Technical Preview, w której możliwość najpierw pojawia się, jak wersja 1804 kwietnia 2018. Te możliwości są wyszczególnione w osobnych tematach dedykowana dla każdej wersji zapoznawczej.  

 Aby uzyskać informacje na temat nowości w wersji current branch programu Configuration Manager, zobacz [nowości w programie System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Wymagania i ograniczenia wersji zapoznawczej Technical Preview  

> [!IMPORTANT]     
>  Wersja zapoznawcza Technical Preview jest licencjonowana tylko do użytku w środowisku laboratoryjnym.  Firma Microsoft nie może udzielać usług pomocy technicznej i niektóre funkcje mogą nie być dostępne w wersji zapoznawczej oprogramowania. Ponadto ograniczona oprogramowania Podgląd lub różnych standardów zabezpieczeń, ochrony prywatności ułatwień dostępu, dostępność i niezawodność względem komercyjnie podane oprogramowania.  

 Dla większości wymagań wstępnych dotyczących produktów, skorzystaj z informacji w [obsługiwane konfiguracje programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md). Do wersji zapoznawczych Technical Preview mają zastosowanie następujące wyjątki:  

-   Każda instalacja pozostaje aktywna przez 90 dni. Następnie staje się nieaktywna.  

-   Jedynym obsługiwanym językiem jest angielski.


-   Obsługiwane są tylko następujące flagi instalacji (przełączniki):  

    -   **/silent**  
    -   **/testdbupgrade**    


-   Domyślnie gdy używasz technical preview instaluje punkt połączenia usługi do trybu online. Nie obsługuje zmiany do trybu offline.

-   Oddzielne artykułów dla każdej określonej wersji technical preview obejmują dodatkowe ograniczenia i wymagania zgodnie z wymaganiami.

-   Brak obsługi migracji do tej kompilacji w wersji zapoznawczej lub z niej.  

-   Brak obsługi uaktualniania do tej kompilacji w wersji zapoznawczej. 

-   Nie jest obsługiwane dla usługi site recovery z folderu cd.latest.  <!--507106-->

-   Brak obsługi uaktualniania z kompilacji w wersji zapoznawczej do kompilacji produkcyjnej (Current Branch). Jednak gdy aktualizacje są dostępne w wersji zapoznawczej, można znaleźć i zainstalować je z **aktualizacje i obsługa** węzła konsoli programu Configuration Manager. Aby obejrzeć film wideo przedstawiający proces uaktualniania w konsoli, zobacz [Installing ConfigMgr Update Packages](https://www.youtube.com/embed/KBd_EGFbUT8) (Instalowanie pakietów aktualizacji programu Configuration Manager) w witrynie youtube.com.  
-   Obsługiwana jest tylko autonomiczna lokacja główna. Brak obsługi centralnej lokacji administracyjnej, wielu lokacji głównych i lokacji dodatkowych.  

Następujące produkty i technologie, są obsługiwane przez gałęzi programu Configuration Manager. Jednak włączenie ich do tej zawartości nie oznacza to rozszerzenia obsługi dla produktu lub wersji, która wykracza poza cykl pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza wsparcia technicznego, nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji na temat cykli wsparcia technicznego firmy Microsoft, zobacz witrynę sieci Web [Cykl wsparcia technicznego produktów firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) .  

-   Obsługiwane są tylko następujące wersje programu SQL Server:  

    -   SQL Server 2017 (z aktualizacją zbiorczą 2 lub nowszej) wprowadzonego w 1710 wersji programu Configuration Manager
    -   SQL Server 2016 (bez dodatku Service Pack i nowsze)
    -   SQL Server 2014 (z dodatkiem Service Pack 1 lub nowszy)
    -   SQL Server 2012 (bez dodatku Service Pack 3 lub nowszej)


-   Lokacja obsługuje do 10 klientów, których musi działać jeden z następujących wersji systemu Windows:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 7  

##  <a name="bkmk_install"></a> Instalowanie i aktualizowanie wersji zapoznawczej Technical Preview  
 Programu System Center Configuration Manager Technical Preview różni się od bieżącej wersji programu System Center Configuration Manager.  

 Aby użyć wersji zapoznawczej technical preview, należy najpierw zainstalować **wersji bazowej** kompilacji wersji zapoznawczej technical preview. Po zainstalowaniu wersji linii bazowej, następnie należy użyć **aktualizacje w konsoli** aby zapewnić, że instalacja aktualne z najnowszą wersją zapoznawczą. Zazwyczaj nowe wersje Technical Preview są dostępne w każdym miesiącu.

Każdej wersji zapoznawczej jest obsługiwany, dopóki dostępne są trzy kolejne wersje. To znaczy, wersja wydana 1708 wersji 1704 nie jest już w obsłudze, ale wersje 1705, 1706 i 1707 pozostała w obsłudze. Linii bazowej przypada poza pomocy technicznej, jest nadal obsługiwane instalowania nowej lokacji Technical Preview, aż do nowej wersji linii bazowej jest dostępna, pod warunkiem, następnie zaktualizuj tę instalację do obsługiwanej wersji. Aktualizowanie do najnowszej dostępnej wersji, a następnie powtórz ten proces, przed zainstalowaniem najnowszej wersji technical preview.

> [!TIP]  
>  Po zainstalowaniu aktualizacji do wersji zapoznawczej technical preview należy zaktualizować instalację wersji wstępnej do nowej wersji technical preview. Instalacji wersji zapoznawczej technical preview nigdy nie ma możliwości uaktualnienia do instalacji current branch ani otrzymania aktualizacji z wersji current branch.  

**Aktywne wersje bazowe Technical Preview:**
   
Można zainstalować wersji linii bazowej maksymalnie jeden rok po ich wydaniu. Jednak podczas instalowania nowej lokacji wersji zapoznawczej technical preview, firma Microsoft zaleca się, że używasz najnowszej wersji linii bazowej, która jest dostępna.
-  **Technical Preview 1711** — Configuration Manager Technical Preview 1711 jest dostępna jako aktualizacja w konsoli, a jako nowej wersji linii bazowej. Pobieranie wersji linii bazowej [ze strony TechNet Evaluation Center](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview).


##  <a name="BKMK_TPFeedback"></a> Przekazywanie opinii  
 Można przyłączyć czekamy na Twoją opinię o możliwościach w wersji zapoznawczych technical Preview. Aby uzyskać więcej informacji, zobacz [opinię o produkcie](../understand/find-help.md#product-feedback).

Jeśli masz pomysły dotyczące nowych funkcji się, że chcesz zobaczyć chcemy wiedzieć, który również. Aby przesłać nowe pomysły i zagłosować na pomysły innych osób, [odwiedź stronę z opiniami użytkowników naszego oprogramowania](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> Możliwości oferowane przez najnowszej wersji zapoznawczej technical preview  
Poniżej przedstawiono możliwości oferowane przez najnowszej wersji programu Configuration Manager w wersji zapoznawczej technical preview.  Funkcje, które były dostępne w poprzedniej wersji technical Preview są dostępne w nowszych wersjach. Podobnie możliwości, które zostały dodane do bieżącej gałęzi programu Configuration Manager pozostają dostępne w wersji zapoznawczych technical preview.  Kliknij informacje o poszczególnych wersjach zapoznawczych, aby uzyskać więcej informacji o określonej możliwości.  

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1804"></a>Technical Preview wersji 1804
- [Konfigurowanie zdalnego biblioteki zawartości na serwerze lokacji](capabilities-in-technical-preview-1804.md#configure-a-remote-content-library-for-the-site-server) <!--1357525--> 
- [Przesyłanie opinii z konsoli programu Configuration Manager](capabilities-in-technical-preview-1804.md#bkmk_feedback) <!--1357542--> 
- [Centrum pomocy technicznej](capabilities-in-technical-preview-1804.md#support-center) <!--1357489--> 
- [Zestaw narzędzi programu Configuration Manager](capabilities-in-technical-preview-1804.md#configuration-manager-toolkit) <!--1357145--> 
- [Odinstaluj aplikację na zatwierdzenie odwołania](capabilities-in-technical-preview-1804.md#uninstall-application-on-approval-revocation) <!--1357891--> 
- [Wyklucz kontenerach usługi Active Directory z odnajdywania](capabilities-in-technical-preview-1804.md#exclude-active-directory-containers-from-discovery) <!--1358143--> 
- [Określ widoczność łącze witryny sieci Web katalogu aplikacji w programie Software Center](capabilities-in-technical-preview-1804.md#specify-the-visibility-of-the-application-catalog-website-link-in-software-center) <!--1358214--> 
- [Filtrowanie reguł automatycznego wdrażania do architektury aktualizacji oprogramowania](capabilities-in-technical-preview-1804.md#filter-automatic-deployment-rules-by-software-update-architecture) <!--1322266--> 
- [Ulepszenia dotyczące wdrażania systemu operacyjnego](capabilities-in-technical-preview-1804.md#improvements-to-os-deployment) <!--1358330,1358493--> 
- [Ulepszenia konsoli programu Configuration Manager](capabilities-in-technical-preview-1804.md#improvements-to-the-configuration-manager-console) <!--510252--> 



## <a name="capabilities-delivered-in-recent-supported-technical-previews"></a>Możliwości oferowane przez ostatnie obsługiwanych wersji zapoznawczych technical Preview
Poniżej przedstawiono możliwości oferowane przez poprzednie wersje wersje technical preview programu Configuration Manager, które nadal są obsługiwane. 

<!-- This is the full list of new features in the past three TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 |Możliwość |Wersji Technical Preview |Bieżącą wersję gałęzi|  
 |----------------|---------------------|--------------------|
 | Dystrybucji ściągania punktów obsługi punktów dystrybucji w chmurze jako źródło <!--1321554--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#pull-distribution-points-support-cloud-distribution-points-as-source)  | ![Nie dodano](media/Red_X.gif) | 
 | Obsługa częściowej pobierania w klienta równorzędnej pamięci podręcznej, aby zmniejszyć wykorzystanie sieci WAN <!--1357346--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#partial-download-support-in-client-peer-cache-to-reduce-wan-utilization)  | ![Nie dodano](media/Red_X.gif) | 
 | Okna obsługi w programie Software Center <!--1358131--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#maintenance-windows-in-software-center)  | ![Nie dodano](media/Red_X.gif) | 
 | Karta niestandardowe dla strony sieci Web w programie Software Center <!--1358132--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#custom-tab-for-webpage-in-software-center)  | ![Nie dodano](media/Red_X.gif) | 
 | Włącz obsługę aktualizacji oprogramowania innych firm na klientach <!--1357605--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#enable-third-party-software-update-support-on-clients)  | ![Nie dodano](media/Red_X.gif) | 
 | Włącz kopiowanie/wklejanie szczegóły zasobu z widokami monitorowania <!--1357552--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#enable-copypaste-of-asset-details-from-monitoring-views)  | ![Nie dodano](media/Red_X.gif) | 
 | Rozszerzenia SCAP <!--1357552--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#scap-extensions)  | ![Nie dodano](media/Red_X.gif) | 
 | Obciążenia programu Endpoint Protection przejścia do usługi Intune przy użyciu wspólnej zarządzania <!-- 1357365 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#transition-endpoint-protection-workload-to-intune-using-co-management) | [Wersja 1802](/sccm/core/clients/manage/co-management-switch-workloads#workloads-able-to-be-transitioned-to-intune) |  
 | Konfigurowanie optymalizacji dostarczania systemu Windows do użycia grup granic w programie Configuration Manager <!-- 1324696 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups) | [Wersja 1802](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization) |  
 | Sekwencji zadań uaktualniania w miejscu systemu Windows 10 za pośrednictwem bramy zarządzania w chmurze <!-- 1357149 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway) | [Wersja 1802](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg) |  
 | Ulepszenia dotyczące sekwencji zadań uaktualniania w miejscu systemu Windows 10 <!-- 1357425 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improvements-to-windows-10-in-place-upgrade-task-sequence) | [Wersja 1802](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system) |  
 | Ulepszenia do punktów dystrybucji z włączoną obsługą środowiska PXE <!-- 1357580 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improvements-to-pxe-enabled-distribution-points) | ![Nie dodano](media/Red_X.gif) | 
 | Szablony wdrażania dla sekwencji zadań <!-- 1357391 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#deployment-templates-for-task-sequences) | [Wersja 1802](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS) |  
 | Produkt cyklu życia w pulpit nawigacyjny <!--1319632 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#product-lifecycle-dashboard) | ![Nie dodano](media/Red_X.gif) | 
 | Ulepszenia dotyczące raportowania <!--1357653 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improvements-to-reporting) | [Wersja 1802](/sccm/core/servers/manage/list-of-reports#operating-system) |  
 | Ulepszenia Centrum oprogramowania <!--1357592 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improvements-to-software-center) | [Wersja 1802](/sccm/core/clients/deploy/about-client-settings#BKMK_HideInstalled) |  
 | Grupy granic rezerwowy dla punktów zarządzania <!-- 1324594 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#boundary-group-fallback-for-management-points) | [Wersja 1802](/sccm/core/servers/deploy/configure/boundary-groups#management-points) |  
 | Ulepszona obsługa certyfikatów CNG <!-- 1357314 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improved-support-for-cng-certificates) | [Wersja 1802](/sccm/core/plan-design/network/cng-certificates-overview) |  
 | Obsługa brama zarządzania usługi Azure Resource Manager w chmurze <!-- 1324735 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#cloud-management-gateway-support-for-azure-resource-manager) | [Wersja 1802](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#azure-resource-manager) |  
 | Zatwierdzanie żądań aplikacji dla użytkowników na urządzenie <!-- 1357015 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#approve-application-requests-for-users-per-device) | [Wersja 1802](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings) |  
 | Przeglądanie i instalowanie aplikacji dostępne dla użytkowników na urządzeniach przyłączonych do usługi AD platformy Azure przy użyciu programu Software Center <!-- 1322613 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices) | [Wersja 1802](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices) |  
 | Raport dotyczący informacji o urządzeniu AutoPilot systemu Windows <!-- 1351442 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#report-on-windows-autopilot-device-information) | [Wersja 1802](/sccm/core/clients/manage/co-management-prepare#new-windows-10-devices) |  
 | Ulepszenia zasad programu Configuration Manager dla usługi Windows Defender wykorzystać zabezpieczenia <!-- 1356220 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard) | [Wersja 1802](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) |  
 | Zasady przeglądarki Microsoft Edge <!-- 1357310 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#microsoft-edge-browser-policies) | [Wersja 1802](/sccm/compliance/deploy-use/browser-profiles) | 
 | Raport dotyczący liczby przeglądarka domyślna <!-- 1357830 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#report-for-default-browser-counts) | [Wersja 1802](/sccm/core/servers/manage/list-of-reports#software---companies-and-products) | 
 | Obsługa urządzeń z systemem Windows 10 ARM64 <!-- 1353704 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#support-for-windows-10-arm64-devices) | [Wersja 1802](/sccm/core/plan-design/configs/support-for-windows-10) |  
 | Tworzenie wdrożenia etapowego <!-- 1356837 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#create-phased-deployments) | [Wersja 1802](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence) |
 | Raportowanie zarządzania wspólnej <!-- 1356648 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#co-management-reporting) | [Wersja 1802](\sccm\core\clients\manage\client-management-dashboard) |
 | Ulepszenia dotyczące harmonogramu oceny reguły wdrażania automatycznego <!-- 1357133 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#improvements-to-automatic-deployment-rule-evaluation-schedule) | [Wersja 1802](/sccm/sum/deploy-use/automatically-deploy-software-updates#BKMK_CreateAutomaticDeploymentRule) |
 | Ponowne przypisanie punktu dystrybucji <!-- 1306937 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#reassign-distribution-point) | [Wersja 1802](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_reassign) |
 | Ulepszenia dotyczące spisu sprzętu <!-- 1357389 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#improvements-to-hardware-inventory) | [Wersja 1802](/sccm/core/clients/manage/inventory/extend-hardware-inventory#BKMK_GreaterThan255) |
 | Udoskonalenia ustawień klienta w programie Software Center <!-- 1355146 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#improvements-to-client-settings-for-software-center) | [Wersja 1802](/sccm/core/clients/deploy/about-client-settings#BKMK_HideUnapproved) |
 | Nowe ustawienia dla systemu Windows Defender aplikacji Guard <!-- 1356256 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#new-settings-for-windows-defender-application-guard) | [Wersja 1802](/sccm/protect/deploy-use/create-deploy-application-guard-policy#BKMK_HIS) |
 | Ulepszenia na uruchamianie skryptów <!-- 1236459 --> | [Podgląd techniczna 1801](capabilities-in-technical-preview-1801.md#improvements-to-run-scripts) | [Wersja 1802](/sccm/apps/deploy-use/create-deploy-scripts) |
 
  

## <a name="capabilities-delivered-in-previous-technical-previews"></a>Możliwości oferowane w poprzednich wersjach technical Preview
Poniżej przedstawiono możliwości oferowane przez poprzednie wersje wersje technical preview programu Configuration Manager. Te funkcje są dostępne w nowszej wersji, ale nie są jeszcze dostępne w wersji current branch. 

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

 |Możliwość |Wersji Technical Preview |  
 |----------------|---------------------|
 | Usługa klienta środowiska PXE <!-- 1357148 --> | [Podgląd techniczna 1712](capabilities-in-technical-preview-1712.md#client-based-pxe-responder-service) |
 |Wysoką dostępność roli serwera lokacji <!-- 1128774 --> |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |
 |Obsługa rozruchu środowiska PXE sieci IPv6 <!-- 1269793 --> |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
 |Użyj usługi Azure Active Directory <!-- 1322145? --> | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
 |Oceny zgodności dla usługi Windows Update dla firm aktualizacji <!-- 1235390 --> | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |
 |Dostęp do danych punktu końcowego OData <!-- 1321523 --> |[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|
 |Ulepszenia dotyczące analizy zasobów <!-- 1307390 --> |[Podgląd techniczna 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|
 |Użytkownicy końcowi mogą instalować aplikacje z portalu firmy <!-- 1037233? --> |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|



## <a name="see-also"></a>Zobacz też  
[Co to jest nowe w programie System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md)

> [!Tip]  
> Aby uzyskać więcej informacji na temat bieżącej gałęzi funkcji, które wymagają zgody włączyć, zobacz [funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).  
> Aby uzyskać więcej informacji na bieżące funkcje gałęzi, które należy najpierw włączyć, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).  

