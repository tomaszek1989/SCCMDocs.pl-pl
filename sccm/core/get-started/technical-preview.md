---
title: Wersje Technical Preview
titleSuffix: Configuration Manager
description: Informacje o wersji Technical Preview, aby test-drive nowe funkcje i możliwości w programie Configuration Manager.
ms.date: 06/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b7372e0b894e93a5a8ec15e54bfeb09e18be6c32
ms.sourcegitcommit: 10a6e3444da631786e9b1729e79a5b728d54ca72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753998"
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

**Zapraszamy do programu System Center Configuration Manager Technical Preview**. Ten artykuł zawiera szczegółowe informacje na temat ewoluującej wersji zapoznawczej, które wprowadza nowe funkcje i możliwości, które firma Microsoft pracuje nad. Każdej wersji technical Preview wprowadzono nowe funkcje, które nie znajdują się w bieżącej gałęzi programu Configuration Manager w momencie udostępnienia wersji zapoznawczej technical preview. Te funkcje mogą zostać później dołączone w aktualizacji wersji Current Branch, ale zanim zostaną ukończone i dodane, chcemy aby mogły zostać wypróbowane przez użytkowników i uzyskać ich opinie.  

 Ponieważ ta wersja jest technical preview, szczegóły i funkcje mogą ulec zmianie.  

 Ten artykuł zawiera informacje, które dotyczą wszystkich wersji Technical Preview. Każda nowa możliwość (lub funkcji) również wyświetlane wraz z wersji zapoznawczej Technical Preview, w której możliwość najpierw pojawia się, jak wersja 1806 czerwca 2018. Te możliwości są wyszczególnione w osobnych tematach dedykowana dla każdej wersji zapoznawczej.  

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
-  **Technical Preview 1806** — Configuration Manager Technical Preview 1806 jest dostępna jako aktualizacja w konsoli, a jako nowej wersji linii bazowej. Pobieranie wersji linii bazowej [ze strony TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview).


##  <a name="BKMK_TPFeedback"></a> Przekazywanie opinii  
 Można przyłączyć czekamy na Twoją opinię o możliwościach w wersji zapoznawczych technical Preview. Aby uzyskać więcej informacji, zobacz [opinię o produkcie](../understand/find-help.md#product-feedback).

Jeśli masz pomysły dotyczące nowych funkcji się, że chcesz zobaczyć chcemy wiedzieć, który również. Aby przesłać nowe pomysły i zagłosować na pomysły innych osób, [odwiedź stronę z opiniami użytkowników naszego oprogramowania](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a> Możliwości oferowane przez najnowszej wersji zapoznawczej technical preview  
Poniżej przedstawiono możliwości oferowane przez najnowszej wersji programu Configuration Manager w wersji zapoznawczej technical preview.  Funkcje, które były dostępne w poprzedniej wersji technical Preview są dostępne w nowszych wersjach. Podobnie możliwości, które zostały dodane do bieżącej gałęzi programu Configuration Manager pozostają dostępne w wersji zapoznawczych technical preview.  Kliknij informacje o poszczególnych wersjach zapoznawczych, aby uzyskać więcej informacji o określonej możliwości.  

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1806"></a>Technical Preview wersji 1806
- [Aktualizacje oprogramowania innych firm](capabilities-in-technical-preview-1806.md#bkmk-3pupdate) <!--1352101-->
- [Skonfiguruj ustawienia systemu Windows Defender SmartScreen Microsoft Edge](capabilities-in-technical-preview-1806.md#configure-windows-defender-smartscreen-settings-for-microsoft-edge) <!--1353701-->
- [Zasady zarządzania urządzeniami Przenośnymi synchronizacji z Microsoft Intune dla wspólnie zarządzanego urządzenia](capabilities-in-technical-preview-1806.md#sync-mdm-policy-from-microsoft-intune-for-a-co-managed-device) <!--1357377-->
- [Obciążenie usługi Office 365 przechodzenia do usługi Intune przy użyciu wspólnej zarządzania](capabilities-in-technical-preview-1806.md#transition-office-365-workload-to-intune-using-co-management) <!--1357841-->
- [Programu Package Conversion Manager](capabilities-in-technical-preview-1806.md#package-conversion-manager) <!--1357861-->
- [Wdrażanie aktualizacji oprogramowania bez zawartości](capabilities-in-technical-preview-1806.md#deploy-software-updates-without-content) <!--1357933-->
- [Integracja narzędzia dostosowywania pakietu Office przy użyciu pakietu Office 365 Instalatora](capabilities-in-technical-preview-1806.md#office-customization-tool-integration-with-the-office-365-installer) <!--1358149-->
- [Ulepszenia zarządzania bramy w chmurze](capabilities-in-technical-preview-1806.md#improvements-to-cloud-management-gateway) <!--1358215,1358651,503899--> 
- [Ulepszenia do zabezpieczania komunikacji z klientem](capabilities-in-technical-preview-1806.md#improvements-to-secure-client-communications) <!--1358278,1358279-->
- [Ulepszenia infrastruktury Centrum oprogramowania](capabilities-in-technical-preview-1806.md#software-center-infrastructure-improvements) <!--1358309-->
- [Zapewnij pakiety aplikacji systemu Windows dla wszystkich użytkowników na urządzeniu](capabilities-in-technical-preview-1806.md#provision-windows-app-packages-for-all-users-on-a-device) <!--1358310-->
- [Udoskonalenia powierzchni pulpitu nawigacyjnego](capabilities-in-technical-preview-1806.md#improvements-to-the-surface-dashboard) <!--1358654-->
- [Poprawki jednostki domyślne spisu sprzętu](capabilities-in-technical-preview-1806.md#hardware-inventory-default-unit-revision) <!--514442-->



## <a name="capabilities-delivered-in-recent-supported-technical-previews"></a>Możliwości oferowane przez ostatnie obsługiwanych wersji zapoznawczych technical Preview
Poniżej przedstawiono możliwości oferowane przez poprzednie wersje wersje technical preview programu Configuration Manager, które nadal są obsługiwane. 

<!-- This is the full list of new features in the past THREE (3) TP releases. 
Each month, add features from the list above to the top of this table. 
Then remove the bottom of this list and/or move individual items not in CB to the third table below.
-->

 |Możliwość |Wersji Technical Preview |Bieżącą wersję gałęzi|  
 |----------------|---------------------|--------------------|
 | Utwórz wdrożenie etapowe z fazy ręcznie skonfigurowanej dla sekwencji zadań <!--1358148--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#create-a-phased-deployment-with-manually-configured-phases-for-a-task-sequence)  | ![Nie dodano](media/Red_X.gif) |  
 | Obsługa punktu dystrybucji chmury dla usługi Azure Resource Manager <!--1322209--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#cloud-distribution-point-support-for-azure-resource-manager)  | ![Nie dodano](media/Red_X.gif) |  
 | Podjąć działania w oparciu o informacje na temat technologii zarządzania <!--1357930--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#take-actions-based-on-management-insights)  | ![Nie dodano](media/Red_X.gif) |  
 | Obciążenie konfiguracji urządzenia przejścia do usługi Intune przy użyciu wspólnej zarządzania <!--1357903--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#transition-device-configuration-workload-to-intune-using-co-management)  | ![Nie dodano](media/Red_X.gif) |  
 | Włącz punkty dystrybucji do użycia kontroli przeciążenia sieci <!--1358112--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#enable-distribution-points-to-use-network-congestion-control)  | ![Nie dodano](media/Red_X.gif) |  
 | Pulpit nawigacyjny zarządzania w chmurze <!--1358461--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#cloud-management-dashboard)  | ![Nie dodano](media/Red_X.gif) |  
 | CMPivot <!--1358456--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#cmpivot)  | ![Nie dodano](media/Red_X.gif) |  
 | Ulepszono klienta bezpiecznej komunikacji <!--1356889,1358228,1358460--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improved-secure-client-communications)  | ![Nie dodano](media/Red_X.gif) |  
 | Ulepszenia włączania obsługi aktualizacji oprogramowania innych firm <!--1357605--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvements-for-enabling-third-party-software-update-support)  | ![Nie dodano](media/Red_X.gif) |  
 | Ulepszenia dotyczące sekwencji zadań uaktualniania w miejscu systemu Windows 10 <!--1358500--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvements-to-windows-10-in-place-upgrade-task-sequence)  | ![Nie dodano](media/Red_X.gif) |  
 | CMTrace zainstalowane z klientem <!--1357971--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#cmtrace-installed-with-client)  | ![Nie dodano](media/Red_X.gif) |  
 | Ulepszenia w konsoli programu Configuration Manager <!--1358202--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvement-to-the-configuration-manager-console)  | ![Nie dodano](media/Red_X.gif) |  
 | Ulepszenia konsoli opinii <!--1357542--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvements-to-console-feedback)  | ![Nie dodano](media/Red_X.gif) |  
 | Ulepszenia do punktów dystrybucji z włączoną obsługą środowiska PXE <!--1357580--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvements-to-pxe-enabled-distribution-points)  | ![Nie dodano](media/Red_X.gif) |  
 | Poprawa spis sprzętu dla dużej liczby całkowite <!--1357880--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvement-to-hardware-inventory-for-large-integer-values)  | ![Nie dodano](media/Red_X.gif) |  
 | Poprawy obsługi usług WSUS <!--1357898--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvement-to-wsus-maintenance)  | ![Nie dodano](media/Red_X.gif) |  
 | Poprawy jakości obsługi w przypadku certyfikatów CNG <!--1357314--> | [Podgląd techniczna 1805](capabilities-in-technical-preview-1805.md#improvement-to-support-for-cng-certificates)  | ![Nie dodano](media/Red_X.gif) |  
| Konfigurowanie zdalnego biblioteki zawartości na serwerze lokacji <!--1357525--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#configure-a-remote-content-library-for-the-site-server)  | ![Nie dodano](media/Red_X.gif) | 
 | Przesyłanie opinii z konsoli programu Configuration Manager <!--1357542--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#bkmk_feedback)  | ![Nie dodano](media/Red_X.gif) | 
 | Centrum pomocy technicznej <!--1357489--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#support-center)  | ![Nie dodano](media/Red_X.gif) | 
 | Zestaw narzędzi programu Configuration Manager <!--1357145--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#configuration-manager-toolkit)  | ![Nie dodano](media/Red_X.gif) | 
 | Odinstaluj aplikację na zatwierdzenie odwołania <!--1357891--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#uninstall-application-on-approval-revocation)  | ![Nie dodano](media/Red_X.gif) | 
 | Wyklucz kontenerach usługi Active Directory z odnajdywania <!--1358143--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#exclude-active-directory-containers-from-discovery)  | ![Nie dodano](media/Red_X.gif) | 
 | Określ widoczność łącze witryny sieci Web katalogu aplikacji w programie Software Center <!--1358214--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#specify-the-visibility-of-the-application-catalog-website-link-in-software-center)  | ![Nie dodano](media/Red_X.gif) | 
 | Filtrowanie reguł automatycznego wdrażania do architektury aktualizacji oprogramowania <!--1322266--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#filter-automatic-deployment-rules-by-software-update-architecture)  | ![Nie dodano](media/Red_X.gif) | 
 | Ulepszenia dotyczące wdrażania systemu operacyjnego <!--1358330,1358493--> | [Podgląd techniczna 1804](capabilities-in-technical-preview-1804.md#improvements-to-os-deployment) | ![Nie dodano](media/Red_X.gif) | 
 | Dystrybucji ściągania punktów obsługi punktów dystrybucji w chmurze jako źródło <!--1321554--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#pull-distribution-points-support-cloud-distribution-points-as-source)  | ![Nie dodano](media/Red_X.gif) | 
 | Obsługa częściowej pobierania w klienta równorzędnej pamięci podręcznej, aby zmniejszyć wykorzystanie sieci WAN <!--1357346--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#partial-download-support-in-client-peer-cache-to-reduce-wan-utilization)  | ![Nie dodano](media/Red_X.gif) | 
 | Okna obsługi w programie Software Center <!--1358131--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#maintenance-windows-in-software-center)  | ![Nie dodano](media/Red_X.gif) | 
 | Karta niestandardowe dla strony sieci Web w programie Software Center <!--1358132--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#custom-tab-for-webpage-in-software-center)  | ![Nie dodano](media/Red_X.gif) | 
 | Włącz obsługę aktualizacji oprogramowania innych firm na klientach <!--1357605--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#enable-third-party-software-update-support-on-clients)  | ![Nie dodano](media/Red_X.gif) | 
 | Włącz kopiowanie/wklejanie szczegóły zasobu z widokami monitorowania <!--1357552--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#enable-copypaste-of-asset-details-from-monitoring-views)  | ![Nie dodano](media/Red_X.gif) | 
 | Rozszerzenia SCAP <!--1357552--> | [Podgląd techniczna 1803](capabilities-in-technical-preview-1803.md#scap-extensions)  | ![Nie dodano](media/Red_X.gif) | 
 
  

## <a name="capabilities-delivered-in-previous-technical-previews"></a>Możliwości oferowane w poprzednich wersjach technical Preview
Poniżej przedstawiono możliwości oferowane przez poprzednie wersje wersje technical preview programu Configuration Manager. Te funkcje są dostępne w nowszej wersji, ale nie są jeszcze dostępne w wersji current branch. 

<!-- This is the list of individual features that are still in TP (not in CB). 
**Note there is no third column in this table!**
Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column)
With each CB release, review and remove from this list for anything that's now available in CB. 
-->

 |Możliwość |Wersji Technical Preview |  
 |----------------|---------------------|
 | Ulepszenia do punktów dystrybucji z włączoną obsługą środowiska PXE <!-- 1357580 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#improvements-to-pxe-enabled-distribution-points) | 
 | Produkt cyklu życia w pulpit nawigacyjny <!--1319632 --> | [Podgląd techniczna 1802](capabilities-in-technical-preview-1802.md#product-lifecycle-dashboard) | 
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

