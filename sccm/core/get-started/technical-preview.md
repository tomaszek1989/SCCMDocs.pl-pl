---
title: Wersje Technical Preview
titleSuffix: Configuration Manager
description: "Więcej informacji o wersji Technical Preview że teraz musisz test-drive nowe funkcje i możliwości w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/15/2017
ms.prod: configuration-manager
ms.reviewer: nab
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9ce0a8cb-f96c-4e41-834c-59ceb54ce44a
caps.latest.revision: "157"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 31daf18a0b276b691e606ea2737ea1838dd8b211
ms.sourcegitcommit: ed8b2438ef85c9160741ef61f9171be41dd1ae0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2017
---
# <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

**Zapraszamy do programu System Center Configuration Manager Technical Preview**. Ten artykuł zawiera szczegółowe informacje na temat ewoluującej wersji zapoznawczej, które wprowadza nowe funkcje i możliwości, które firma Microsoft pracuje nad. Każdej wersji technical Preview wprowadzono nowe funkcje, które nie znajdują się w bieżącej gałęzi programu Configuration Manager w momencie udostępnienia wersji zapoznawczej technical preview. Te funkcje mogą zostać później dołączone w aktualizacji wersji Current Branch, ale zanim zostaną ukończone i dodane, chcemy aby mogły zostać wypróbowane przez użytkowników i uzyskać ich opinie.  

 Ponieważ ten temat dotyczy wersji zapoznawczej Technical Preview, szczegóły i funkcje mogą ulec zmianie.  

 Ten artykuł zawiera informacje, które dotyczą wszystkich wersji Technical Preview. Każda nowa możliwość (lub funkcji) również wyświetlane wraz z wersji zapoznawczej Technical Preview, w której możliwości najpierw pojawia się, jak wersja 1712 grudnia 2017 r. Te możliwości są wyszczególnione w osobnych tematach dedykowana dla każdej wersji zapoznawczej.  

 Aby uzyskać informacje na temat nowości w wersji current branch programu Configuration Manager, zobacz [nowości w programie System Center Configuration Manager](/sccm/core/plan-design/changes/what-has-changed-from-configuration-manager-2012).



##  <a name="bkmk_reqs"></a> Wymagania i ograniczenia wersji zapoznawczej Technical Preview  

> [!IMPORTANT]     
>  Wersja zapoznawcza Technical Preview jest licencjonowana tylko do użytku w środowisku laboratoryjnym.  Firma Microsoft może zatem nie świadczyć usług pomocy technicznej związanych z tą wersją, a określone funkcje mogą być niedostępne w wersji zapoznawczej oprogramowania. Ponadto ograniczona oprogramowania Podgląd lub różnych standardów zabezpieczeń, ochrony prywatności ułatwień dostępu, dostępność i niezawodność względem komercyjnie podane oprogramowania.  

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

-   Brak obsługi uaktualniania z kompilacji w wersji zapoznawczej do kompilacji produkcyjnej (Current Branch). Jednak gdy aktualizacje są dostępne w wersji zapoznawczej, można znaleźć i zainstalować je z **aktualizacje i obsługa** węzła konsoli programu Configuration Manager. Aby obejrzeć film wideo przedstawiający proces uaktualniania w konsoli, zobacz [Installing ConfigMgr Update Packages](https://www.youtube.com/embed/KBd_EGFbUT8) (Instalowanie pakietów aktualizacji programu Configuration Manager) w witrynie youtube.com.  
-   Obsługiwana jest tylko autonomiczna lokacja główna. Brak obsługi centralnej lokacji administracyjnej, wielu lokacji głównych i lokacji dodatkowych.  

Następujące produkty i technologie, są obsługiwane przez gałęzi programu Configuration Manager. Jednak włączenie ich do tej zawartości nie oznacza to rozszerzenia obsługi dla produktu lub wersji, która wykracza poza cykl pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza wsparcia technicznego, nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji na temat cykli wsparcia technicznego firmy Microsoft, zobacz witrynę sieci Web [Cykl wsparcia technicznego produktów firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) .  

-   Obsługiwane są tylko następujące wersje programu SQL Server:  

    -   SQL Server 2016 (bez dodatku Service Pack i nowsze)
    -   SQL Server 2014 (z dodatkiem Service Pack 1 lub nowszy)
    -   SQL Server 2012 (bez dodatku Service Pack 3 lub nowszej)


-   Lokacja obsługuje do 10 klientów, których musi działać jeden z następujących wersji systemu Windows:  

      -   Windows 10  
      -   Windows 8.1  
      -   Windows 8  
      -   Windows 7  

##  <a name="bkmk_install"></a> Instalowanie i aktualizowanie wersji zapoznawczej Technical Preview  
 Programu System Center Configuration Manager Technical Preview różni się od bieżącej wersji programu System Center Configuration Manager.  

 Aby użyć wersji zapoznawczej technical preview, należy najpierw zainstalować **wersji bazowej** kompilacji wersji zapoznawczej technical preview. Po zainstalowaniu wersji bazowej należy uaktualnić tę kompilację za pomocą **aktualizacji w konsoli** , aby upewnić się, że instalacja będzie zgodna z najnowszą wersją zapoznawczą. Zazwyczaj nowe wersje Technical Preview są dostępne w każdym miesiącu.

Każdej wersji zapoznawczej jest obsługiwany, dopóki dostępne są trzy kolejne wersje. To znaczy, wersja wydana 1708 wersji 1704 nie jest już w obsłudze, ale wersje 1705, 1706 i 1707 pozostała w obsłudze. Linii bazowej przypada poza pomocy technicznej, jest nadal obsługiwane instalowania nowej lokacji Technical Preview, aż do nowej wersji linii bazowej jest dostępna, pod warunkiem, następnie zaktualizuj tę instalację do obsługiwanej wersji. Aktualizowanie do najnowszej dostępnej wersji, a następnie powtórz ten proces, przed zainstalowaniem najnowszej wersji technical preview.

> [!TIP]  
>  Po zainstalowaniu aktualizacji wersji zapoznawczej Technical Preview należy zaktualizować instalację wersji wstępnej do nowej wersji zapoznawczej Technical Preview.    W przypadku instalacji wersji zapoznawczej Technical Preview nigdy nie ma możliwości uaktualnienia do instalacji Current Branch ani otrzymania aktualizacji z wersji Current Branch.  

**Aktywne wersje bazowe Technical Preview:**  
Można zainstalować wersji linii bazowej maksymalnie jeden rok po ich wydaniu. Jednak podczas instalowania nowej lokacji wersji zapoznawczej technical preview, firma Microsoft zaleca się, że używasz najnowszej wersji linii bazowej, która jest dostępna.
-  **Technical Preview 1711** — Configuration Manager Technical Preview 1711 jest dostępna jako aktualizacja w konsoli, a jako nowej wersji linii bazowej. Pobieranie wersji linii bazowej [ze strony TechNet Evaluation Center](http://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection-technical-preview).


##  <a name="BKMK_TPFeedback"></a> Przekazywanie opinii  
 Czekamy na Twoją opinię na temat wersji zapoznawczych Technical Preview. Aby przesłać opinię na temat funkcji poszczególnych wersji zapoznawczych, skorzystaj z linku do formularza opinii na stronie [programu przekazywania opinii dotyczących programu Configuration Manager](https://connect.microsoft.com/ConfigurationManagervnext/Feedback) w witrynie Microsoft Connect.  

 Czekamy też na pomysły dotyczące nowych funkcji. Aby przesłać nowe pomysły i zagłosować na pomysły innych osób, [odwiedź stronę z opiniami użytkowników naszego oprogramowania](http://configurationmanager.uservoice.com).  

<!--   ##  <a name="bdmk_tpknownissues"></a> General changes introduced in Technical Previews    -->




##  <a name="bkmk_tpCaps"></a>Możliwości oferowane przez najnowszej wersji zapoznawczej technical preview  
Poniżej przedstawiono możliwości oferowane przez najnowszej wersji programu Configuration Manager w wersji zapoznawczej technical preview.  Funkcje, które były dostępne w poprzedniej wersji technical Preview są dostępne w nowszych wersjach. Podobnie możliwości, które zostały dodane do bieżącej gałęzi programu Configuration Manager pozostają dostępne w wersji zapoznawczych technical preview.  Kliknij informacje o poszczególnych wersjach zapoznawczych, aby uzyskać więcej informacji o określonej możliwości.  

<!-- This is the full list of new features in the latest TP release -->

### <a name="technical-preview-version-1712"></a>Technical Preview wersji 1712
- [Nie uaktualniaj automatycznie zastępowanej aplikacji](capabilities-in-technical-preview-1712.md#do-not-automatically-upgrade-superseded-applications)<!-- 1351266 --> 
- [Zainstaluj wiele aplikacji w programie Software Center](capabilities-in-technical-preview-1712.md#install-multiple-applications-in-software-center)<!-- 1357126 --> 
- [Zmiany w kliencie programu Configuration Manager zainstalować](capabilities-in-technical-preview-1712.md#change-in-the-configuration-manager-client-install)<!-- 1356195 --> 
- [Zmień na pulpicie nawigacyjnym powierzchni urządzenia](capabilities-in-technical-preview-1712.md#change-to-the-surface-device-dashboard)<!-- 1355788 --> 
- [Ulepszenia zarządzania usługi Office 365 klienta pulpitu nawigacyjnego](capabilities-in-technical-preview-1712.md#improvements-to-office-365-client-management-dashboard)<!-- 1357281 --> 
- [Ulepszenia konsoli programu Configuration Manager](capabilities-in-technical-preview-1712.md#improvements-to-the-configuration-manager-console)<!-- 1357280,1357282 --> 
- [Ulepszenia dotyczące wdrażania systemu operacyjnego](capabilities-in-technical-preview-1712.md#improvements-to-operating-system-deployment)<!-- SMS 500897 --> 
- [Integracja aplikacji systemu Windows 10 opinii Centrum](capabilities-in-technical-preview-1712.md#windows-10-feedback-hub-app-integration)<!-- NA -->




## <a name="capabilities-delivered-in-recent-supported-technical-previews"></a>Możliwości oferowane przez ostatnie obsługiwanych wersji zapoznawczych technical Preview
Poniżej przedstawiono możliwości oferowane przez poprzednie wersje wersje technical preview programu Configuration Manager, które nadal są obsługiwane. 

<!-- This is the full list of new features in the past three TP releases. Each month, add features from the list above to the top of this table. Then remove the bottom of this list (and/or move individual items not in CB to the third table below). -->

 |Możliwość |Wersji Technical Preview |Bieżącą wersję gałęzi|  
 |----------------|---------------------|--------------------|
 |Uruchom sekwencję zadań<!-- 1261338 --> | [Podgląd techniczna 1711](capabilities-in-technical-preview-1711.md) |[Wersja 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence)    |
 |Zezwala na interakcję użytkownika podczas instalowania aplikacji<!-- 1356976 --> | [Podgląd techniczna 1711](capabilities-in-technical-preview-1711.md) |![Nie dodano](media/Red_X.gif)    |
 |Dane telemetryczne systemu Windows 10 dotyczące kondycji urządzeń Analytics systemu Windows<!--1356148 --> | [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md#limit-windows-10-enhanced-telemetry-to-only-send-data-relevant-to-windows-analytics-device-health) |[Wersja 1710](/sccm/core/plan-design/changes/whats-new-in-version-1710#reporting)    |
 |Ulepszenia Centrum oprogramowania ikon<!-- 1356194 --> | [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md#software-center-no-longer-distorts-icons-larger-than-250x250) |[Wersja 1710](/sccm/apps/plan-design/plan-for-and-configure-application-management#supplemental-procedures-to-install-and-configure-the-application-catalog-and-software-center)    |
 |Sprawdź zgodność z Centrum oprogramowania dla tej samej zarządzanych urządzeń<!-- 1356374 -->|[Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md#check-compliance-from-software-center-for-co-managed-devices)|[Wersja 1710](/sccm/core/clients/manage/co-management-overview)    |
 |Ograniczona obsługa certyfikatów CNG<!-- 1356191 -->| [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md#limited-support-for-cng-certificates)|[Wersja 1710](/sccm/core/plan-design/network/cng-certificates-overview)    |
 |Obsługa wykorzystać zabezpieczenia<!--1355468 --> | [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md#support-for-exploit-guard) |[Wersja 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy)    |
 |Ulepszone opisy do czasu ponownego uruchomienia komputera<!-- 1356283  -->| [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md)|[Wersja 1710](/sccm/core/clients/manage/manage-clients)    |
 |Zmiany zasad ochrona urządzeń<!-- 1355092  -->| [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md)|[Wersja 1710](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)    |
 |Konfigurowanie i wdrażanie zasad Guard aplikacji programu Windows Defender<!-- 1351960  -->| [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md)|[Wersja 1710](/sccm/protect/deploy-use/create-deploy-application-guard-policy)    |
 |Ulepszenia dotyczące wdrażania skryptów programu PowerShell z programu Configuration Manager<!-- 1236459 -->| [Podgląd techniczna 1710](capabilities-in-technical-preview-1710.md#improvements-for-deploying-powershell-scripts-from-configuration-manager) | [Wersja 1710](/sccm/apps/deploy-use/create-deploy-scripts)
 |VPN udoskonalone środowisko profilu w konsoli programu Configuration Manager<!-- 1313282 --> | [Podgląd techniczna 1709](capabilities-in-technical-preview-1709.md) |![Nie dodano](media/Red_X.gif)    |
 |Jednoczesne zarządzania dla urządzeń z systemem Windows 10|[Podgląd techniczna 1709](capabilities-in-technical-preview-1709.md#co-management-for-windows-10-devices)|[Wersja 1710](/sccm/core/clients/manage/co-management-overview.md)|
 

## <a name="capabilities-delivered-in-previous-technical-previews"></a>Możliwości oferowane w poprzednich wersjach technical Preview
Poniżej przedstawiono możliwości oferowane przez poprzednie wersje wersje technical preview programu Configuration Manager. Te funkcje są dostępne w nowszej wersji, ale nie są jeszcze dostępne w wersji current branch. 

<!-- This is the list of individual features that are still in TP (not in CB). Note there is no third column in this table! Each month review and remove from this list for anything that's now available in CB. Copy from the bottom of the list above any individual feature that is still in TP and add to the top of this list (then remove the third column) -->

 |Możliwość |Wersji Technical Preview |  
 |----------------|---------------------|
 |Informacje na temat technologii zarządzania<!-- 1353967 --> |[Podgląd techniczna 1708](capabilities-in-technical-preview-1708.md#management-insights)|
 |Powierzchni urządzenia pulpitu nawigacyjnego<!-- 1355788 --> |[Podgląd techniczna 1707](capabilities-in-technical-preview-1707.md#surface-device-dashboard)|
 |Wysoką dostępność roli serwera lokacji<!-- 1128774 --> |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#site-server-role-high-availability) |
 |Obsługa rozruchu środowiska PXE sieci IPv6<!-- 1269793 --> |[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#pxe-network-boot-support-for-ipv6)|
 |Ocena zaświadczania o kondycji urządzenia dla zasady zgodności dla dostępu warunkowego<!-- 1235616 -->|[Podgląd techniczna 1706](capabilities-in-technical-preview-1706.md#device-health-attestation-assessment-for-compliance-policies-for-conditional-access)|
 |Użyj usługi Azure Active Directory<!-- 1322145? --> | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#azurediscovery) |
 |Oceny zgodności dla usługi Windows Update dla firm aktualizacji<!-- 1235390 --> | [Podgląd techniczna 1702](capabilities-in-technical-preview-1702.md#compliance-assessment-for-windows-update-for-business-updates) |
 |Dostęp do danych punktu końcowego OData<!-- 1321523 --> |[Podgląd techniczna 1612](capabilities-in-technical-preview-1612.md#odata-endpoint-data-access)|
 |Ulepszenia dotyczące analizy zasobów<!-- 1307390 --> |[Podgląd techniczna 1608](capabilities-in-technical-preview-1608.md#improvements-to-asset-intelligence)|
 |Użytkownicy końcowi mogą instalować aplikacje z portalu firmy<!-- 1037233? --> |[Podgląd techniczna 1605](capabilities-in-technical-preview-1605.md#BKMK_End)|





## <a name="see-also"></a>Zobacz też  
[Co to jest nowe w programie System Center Configuration Manager](/sccm/core/plan-design/changes/whats-new-incremental-versions)  
 [Wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md)
