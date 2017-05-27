---
title: "Która gałąź należy używać | Dokumentacja firmy Microsoft"
description: "Dowiedz się z różnicami w gałęzi dostępne programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: f791278b0aa8efc734a894da7dab1704bb567ed0
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>Która gałąź programu Configuration Manager należy użyć?

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi, długoterminowej obsługi gałęzi i Technical Preview)*


Począwszy od października 2016, istnieją trzy gałęzie programu System Center Configuration Manager dostępna. Użyj w tym temacie w celu wybrania gałęzi odpowiednie dla Ciebie.

> [!TIP]  
> Wszystkie lokacje w hierarchii, należy uruchomić tego samego gałęzi. Mają hierarchię o różnych gałęzi w różnych lokacjach nie jest obsługiwane.

## <a name="current-branch-of-system-center-configuration-manager"></a>Bieżącej gałęzi programu System Center Configuration Manager
Jest to licencjonowanego gałęzi do użytku w środowisku produkcyjnym, w której chcesz opcję, aby pobrać najnowsze funkcje i funkcje. Jest to gałęzi do użycia w przypadku korzystania z jednej z następujących czynności: Centrum danych programu System Center, System Center Standard, System Center Configuration Manager lub prawa równoważne subskrypcji. Aby uzyskać więcej informacji o Software Assurance i opcji licencjonowania, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](learn-more-editions.md).


>  [!TIP]
> Można zainstalować bieżącej gałęzi w wersji ewaluacyjnej, który nie wymaga licencji. Wersja ewaluacyjna może służyć do 180 dni i obsługuje uaktualnienie do wersji licencjonowanej bieżącej gałęzi.

Bieżącej gałęzi są aktualizowane kilka razy w roku z nowych funkcji. Każda wersja aktualizacji jest obsługiwana przez jeden rok po jego wydaniu. Należy zaktualizować do nowszej wersji bieżącej gałęzi w lub przed wygaśnięciem okresu rocznego. Aktualizacje do nowszych wersji są dostępne aktualizacje w konsoli.

Aby zainstalować bieżącej gałęzi jako nową witrynę lub jako aktualizację wydania System Center 2012 Configuration Manager z dodatkiem Service Pack 2 lub System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1, należy użyć [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) programu System Center Configuration Manager dołączony jako dysk DVD z System Center 2016, lub które są dostępne jako część autonomiczna wersja programu System Center Configuration Manager. Dostęp do tego nośnika zależy od tego, jak mieć licencję programu System Center Configuration Manager. Nowsze wersje linii bazowej, tak jak 1702 nie obsługują instalacji z LTSB.

Umożliwia także nośnika linii bazowej do zainstalowania nowej lokacji, która jest w wersji ewaluacyjnej programu bieżącej gałęzi. Jeśli chcesz zainstalować wersję ewaluacyjną, można uzyskać przez oprogramowanie [Centrum ewaluacji TechNet](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection) witryny sieci Web.

>  [!NOTE]
> Nośnik linii bazowej umożliwia zainstalowanie lokacji do nowej hierarchii programu Configuration Manager. Jeśli wcześniej została zainstalowana wersja linii bazowej, podobnie jak w wersji 1511, zaktualizuj swoje witryny do nowej wersji, takich jak 1606 za pomocą funkcji Aktualizacje w konsoli.
>
> Lokacje, które są aktualizowane przy użyciu wynik aktualizacji w lokacji, które są takie same, jak nowej lokacji zainstalowany przy użyciu nośnika linii bazowej w konsoli.
>
> Aby uzyskać więcej informacji, zobacz [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

**Funkcje bieżącej gałęzi**
- Odbiera [aktualizacji w konsoli](/sccm/core/servers/manage/install-in-console-updates) nowych funkcji ułatwiających dostępne do użycia.
- Odbiera aktualizacji w konsoli, które dostarczania zabezpieczeń i jakości poprawki do istniejących funkcji.
- Obsługuje aktualizacje poza pasmem, gdy jest to konieczne. Zobacz [za pomocą narzędzia rejestracji aktualizacji](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) lub [korzystanie z instalatora poprawek](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates).
- Może współpracować z Microsoft Intune i innych usług w chmurze i infrastruktury.
- Obsługuje [migracji danych](/sccm/core/migration/migrate-data-between-hierarchies) do i z innych instalacji programu Configuration Manager.
- Obsługuje uaktualnienie z poprzednich wersji programu Configuration Manager.
- Obsługuje instalację w wersji ewaluacyjnej, z którego można później uaktualnić do w pełni licencjonowaną instalacji.

Początkowa wersja bieżącej gałęzi była wersja 1511. Kolejne aktualizacje obejmują 1606 wersje 1602 i tak dalej. Każda wersja pozostaje w pomocy technicznej przez jeden rok, a firma Microsoft zaleca aktualizację do najnowszej wersji wkrótce po jego wydaniu. Można poczekać do jednego roku przed zaktualizowaniem do nowszej wersji i zainstalowanie najnowszej wersji dostępnej aktualizacji możesz też pominąć. Ponieważ każda wersja jest zbiorczą, jeśli pominąć aktualizacji i zainstaluj najnowszą wersję, nadal uzyskasz dostęp do wszystkich funkcji i ulepszeń z poprzednich wersji.

Aby uzyskać więcej informacji, zobacz [obsługę wersji bieżącej gałęzi](/sccm/core/servers/manage/current-branch-versions-supported).

**Opcje aktualizacji**
- Z aktywnym pakietem Software Assurance można zainstalować aktualizacji w konsoli dla wersji bieżącej gałęzi.  
- Nie ma żadnej opcji, aby przekonwertować bieżącej gałęzi Technical Preview. Podglądy techniczne są oddzielnych instalacji, które nie wymagają licencji.
- Nie ma żadnych opcji przekonwertować aktualna gałąź do długoterminowej obsługi gałęzi (LTSB). Należy odinstalować bieżącej gałęzi, a następnie zainstalować LTSB jako nową instalację.

##  <a name="long-term-servicing-branch-of-system-center-configuration"></a>Długoterminowe gałęzi obsługi konfiguracji programu System Center
Jest to licencjonowanego gałęzi do użycia w produkcji dla klientów programu Configuration Manager, którzy korzystają z bieżącej gałęzi i pozwala uzyskać ich Configuration Manager Software Assurance (SA) lub prawa równoważne subskrypcja wygaśnie po 1 października 2016. Aby uzyskać więcej informacji o Software Assurance i opcji licencjonowania, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](learn-more-editions.md).

LTSB jest oparte na wersji 1606. Tej gałęzi nie otrzymywać aktualizacje w konsoli, które dostarczania nowych funkcji lub aktualizowanie istniejących możliwości. Jednak znajdują się poprawki zabezpieczeń krytyczne. Aby zainstalować LTSB, należy użyć wersji 1606 [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) aby można było uzyskać jako dysk DVD z System Center 2016 lub System Center Configuration Manager.

Aby zainstalować LTSB jako nową witrynę lub uaktualnienia z obsługiwanej lokacji programu Configuration Manager 2012, należy użyć wersji 1606 [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) aby można było uzyskać jako dysk DVD z System Center 2016 lub wersji programu System Center Configuration Manager (bieżącej gałęzi i długoterminowe obsługi gałęzi 1606). Nośnik linii bazowej służy do instalowania nowej lokacji, która jest uruchamiana wersja 1606 bieżącej gałęzi lub nowej lokacji z uruchomionym długoterminowe obsługi gałęzi.

> [!TIP]  
> Aby dowiedzieć się więcej o programie System Center 2016, zobacz [dokumentacji programu System Center 2016](https://technet.microsoft.com/system-center-docs/system-center). Ta dokumentacja identyfikuje również jak System Center 2016, co wymaga umowy licencyjnej firmy Microsoft lub podobne prawa.

> Aby znaleźć System Center Configuration Manager w wersji 1606 w Volume Licensing Service Center (VLSC), przejdź do **pliki do pobrania i klucze** na karcie [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), wyszukaj "system center config", a następnie wybierz **System Center Config Mgr (bieżącej gałęzi i LTSB 1606)**.

> Można również uzyskać wersji ewaluacyjnej programu System Center 2016 z [Centrum ewaluacji TechNet](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview).

**Funkcje LTSB**
-    Odbiera dostarczenia poprawki zabezpieczeń krytyczne aktualizacje w konsoli
- Udostępnia opcję instalacji, jeśli wygasły Twoje umowy lub równoważne uprawnienia SA do programu Configuration Manager
- Obsługuje uaktualnienie (konwersji) do bieżącego rozgałęzienia, gdy masz bieżącej umowy SA lub odpowiednie prawa dostępu do programu Configuration Manager

**Ograniczenia**  
LTSB zależy od wersji bieżącej gałęzi 1606 i ma następujące ograniczenia:
- LTSB nie jest obsługiwane przez 10 lat krytyczne aktualizacje zabezpieczeń po jego dostępność ogólne (październik 2016), po, pomocy technicznej dla tej gałęzi wygaśnie. Aby uzyskać więcej informacji o zasady świadczenia pomocy technicznej, zobacz [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).
- Obsługuje ograniczony zestaw listę systemów operacyjnych serwera i klienta i powiązanych technologii, takich jak wersji programu SQL Server. Aby uzyskać więcej informacji o to, co jest obsługiwane w tej gałęzi, zobacz [Supported Configurations for gałęzi obsługi długoterminowe](supported-configurations-for-ltsb.md).
- Nie otrzymywać aktualizacje dla nowych funkcji.
- Nie obsługuje dodawania subskrypcja usługi Microsoft Intune, co uniemożliwia użycie:
  -    Usługa Intune w konfiguracji oprogramowania MDM hybrydowych
 - Lokalnie MDM
-    Program nie obsługuje pulpitu nawigacyjnego systemu Windows 10 obsługi, obsługi planów, Windows 10 bieżącej gałęzi CB lub bieżącej gałęzi firmy (CBB).
- Nie obsługuje przyszłych wersjach systemu Windows 10 LTSB i systemu Windows Server.
-    Analiza zasobów nie są obsługiwane.
-    Punkty dystrybucji w chmurze nie są obsługiwane.
-    Obsługa programu Exchange Online jako łącznika programu Exchange nie są obsługiwane.
-    Nie obsługuje wszystkie funkcje wersji wstępnej.



**Opcje aktualizacji**
- Instalacja programu LTSB można przekonwertować instalacji bieżącej gałęzi. Konwersja do bieżącej gałęzi jest obsługiwana przed lub po pomocy technicznej dla LTSB wygaśnie.

  Aby dokonać konwersji, musi mieć aktywne umowy Software Assurance z firmą Microsoft. Aby uzyskać więcej informacji zobacz następujące łącza:
  - [Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi](convert-to-current-branch.md)
  - [Licencjonowanie i gałęzie dla programu System Center Configuration Manager](learn-more-editions.md)
  - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#baseline-and-update-versions) w [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates)
- Nie ma żadnych opcji, aby przekonwertować LTSB Technical Preview. Podglądy techniczne są oddzielnych instalacji, które nie wymagają licencji.
-    Nie można uaktualnić wersję ewaluacyjną bieżącej gałęzi do instalacji LTSB.


## <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager
Technical Preview jest dostępny do użycia w środowisku laboratoryjnym, które chcesz więcej informacji na temat i wypróbuj najnowsze funkcje opracowywane dla programu Configuration Manager. Technical Preview nie jest obsługiwana w środowisku produkcyjnym i nie wymaga posiadania Software Assurance umowy licencyjnej.

Aby zainstalować nową witrynę działającą Technical Preview, użyj najnowszej [linii bazowej nośnika dla programu System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview). Po zainstalowaniu Technical Preview nowe wersje są dostępne jako aktualizacji w konsoli co miesiąc.

**Funkcje Technical Preview**
-  Oparte na najnowszych wersji linii bazowej bieżącej gałęzi
-  Odbiera aktualizacji w konsoli, które aktualizacji instalacji do najnowszej wersji Technical Preview
-  Zawiera nowe funkcje, które są opracowywane i dla którego naszych deweloperów chcesz swoją opinię
-  Odbiera aktualizacje, które mają zastosowanie tylko do gałęzi Technical Preview

**Ograniczenia**
-  [Obsługa jest ograniczona](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview), łącznie z tylko jednej lokacji głównej i maksymalnie 10 klientów.  
-  Nie można uaktualnić do bieżącej gałęzi lub LTSB.
-  Nie obsługuje importowania lub eksportowania danych do innej instalacji programu Configuration Manager za pomocą migracji.
-  Nie obsługuje uaktualnienia z poprzedniej wersji programu Configuration Manager.
-  Nie obsługuje instalacji w wersji ewaluacyjnej.

Funkcje, które zostały najpierw wprowadzone w Technical Preview często są dodawane do bieżącej gałęzi w nowszych aktualizacji. Każda nowa wersja Technical Preview zawiera funkcje z poprzednich wersji zapoznawczych techniczne, nawet po te funkcje zostały dodane do bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).

**Opcje aktualizacji**
-    Można zainstalować jakichkolwiek aktualizacji w konsoli dla nowej wersji Technical Preview.
-    Nie ma żadnej opcji, aby przekonwertować bieżącej gałęzi lub LTSB Technical Preview.


## <a name="identify-your-branch-and-version"></a>Identyfikowanie gałęzi i wersji
Podczas wyświetlania informacji o wersji dla lokacji programu Configuration Manager można również upewnić gałęzi.

**Wersja**   
Sprawdzanie wersji witryny, w konsoli, przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli gdzie **wersja lokacji** pojawi się. Zobacz [ ]() listę wersje lokacji.

**Gałęzi**  
Aby potwierdzić gałęzi witryny (jako LTSB lub bieżącej gałęzi), w konsoli, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**i Otwórz **ustawienia hierarchii**. Jeśli istnieje opcja konwersji bieżącej gałęzi i jest aktywna, witryna jest uruchamiana wersja LTSB. Po uruchomieniu bieżącej gałęzi lokacji tej opcji jest niedostępny.
Informacje o różnych wersjach programu Configuration Manager, zobacz "linii bazowej i aktualizacji wersji" w [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates).

