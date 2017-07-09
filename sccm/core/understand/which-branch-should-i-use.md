---
title: "Która gałąź należy używać | Dokumentacja firmy Microsoft"
description: "Dowiedz się różnic między dostępne gałęzi programu System Center Configuration Manager."
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
ms.sourcegitcommit: 662901e850566756759fcfc61c58f3c0e56bc5aa
ms.openlocfilehash: 26356a80bd8c78d4517253bae73e53d8d8f3a73a
ms.contentlocale: pl-pl
ms.lasthandoff: 06/03/2017


---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>Które gałęzi programu Configuration Manager należy użyć?

*Dotyczy: System Center Configuration Manager (Current Branch, długoterminowe gałęzi obsługi i Technical Preview)*


Począwszy od października 2016, istnieją trzy gałęzie programu System Center Configuration Manager dostępne. Użyj tego tematu, aby wybrać prawa gałęzi.

> [!TIP]  
> Wszystkie lokacje w hierarchii należy uruchomić na tym samym oddziale. Mieć hierarchii o różnych gałęziach w różnych lokacjach nie jest obsługiwane.

## <a name="current-branch-of-system-center-configuration-manager"></a>Bieżąca gałąź programu System Center Configuration Manager
To jest licencjonowane gałęzi do użycia w środowisku produkcyjnym, w którym ma być opcję, aby uzyskać najnowsze funkcje i funkcje. To jest gałąź do użycia w przypadku jednego z następujących czynności: System Center Datacenter, System Center standardowe, System Center Configuration Manager lub równoważne subskrypcji. Aby uzyskać więcej informacji o Software Assurance i opcje licencjonowania, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](learn-more-editions.md).


>  [!TIP]
> Bieżąca gałąź można zainstalować w wersji ewaluacyjnej, która nie wymaga licencji. Wersja ewaluacyjna może służyć do 180 dni i obsługuje uaktualnienie do wersji licencjonowanej bieżącej gałęzi.

Bieżąca gałąź jest aktualizowana kilka razy w roku z nowych funkcji. Każda wersja aktualizacji jest obsługiwana przez jeden rok po ich wydaniu. Należy zaktualizować do nowszej wersji Current Branch na lub przed wygaśnięciem okresu rocznego. Aktualizacje do nowszych wersji są dostępne jako aktualizacje w konsoli.

Aby zainstalować bieżącej gałęzi jako nową lokację lub uaktualnienie z programu System Center 2012 Configuration Manager z dodatkiem Service Pack 2 lub System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1, należy użyć [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) programu System Center Configuration Manager dołączony jako dysk DVD z programem System Center 2016 lub które są dostępne jako część autonomiczna wersja programu System Center Configuration Manager. Dostęp do tego nośnika zależy od tego, jak ma licencję programu System Center Configuration Manager. Nowsze wersje linii bazowej, takich jak 1702 nie obsługują instalację LTSB.

Umożliwia także nośnika linii bazowej w celu zainstalowania nowej lokacji, który jest w wersji próbnej bieżącej gałęzi. Jeśli chcesz zainstalować wersję ewaluacyjną, możesz pobrać oprogramowanie z [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection) witryny sieci Web.

>  [!NOTE]
> Do zainstalowania lokacji dla nowej hierarchii programu Configuration Manager, należy użyć nośnika linii bazowej. Jeśli wcześniej zainstalowano wersji linii bazowej, podobnie jak w wersji 1511, należy użyć aktualizacji w konsoli, aby zaktualizować lokacji do nowej wersji, takich jak 1606.
>
> Lokacje, które są aktualizowane przy użyciu wynik aktualizacji w lokacji, które są takie same jak nowej lokacji zainstalowane za pomocą nośnika linii bazowej w konsoli.
>
> Aby uzyskać więcej informacji, zobacz [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

**Funkcje bieżącej gałęzi**
- Odbiera [aktualizacje w konsoli](/sccm/core/servers/manage/install-in-console-updates) który udostępnia nowe funkcje do użycia.
- Odbiera aktualizacje w konsoli, które dostarczać aktualizacje zabezpieczeń oraz poprawki jakości istniejących funkcji.
- Obsługuje aktualizacje poza pasmem, gdy jest to konieczne. Zobacz [używanie narzędzia rejestracji aktualizacji](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) lub [przy użyciu instalatora poprawek](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates).
- Może współdziałać z Microsoft Intune i innych usług w chmurze i infrastruktury.
- Obsługuje [migracji danych](/sccm/core/migration/migrate-data-between-hierarchies) do i z innych instalacji programu Configuration Manager.
- Program obsługuje uaktualnienie z poprzednich wersji programu Configuration Manager.
- Obsługuje instalację w wersji ewaluacyjnej, z którego można później uaktualnić do w pełni licencjonowanej instalacji.

Początkowa wersja Current Branch był w wersji 1511. Kolejne aktualizacje obejmują 1606 wersji 1602 i tak dalej. Każda wersja pozostaje w pomocy technicznej przez jeden rok, i firma Microsoft zaleca aktualizacji do najnowszej wersji wkrótce po ich wydaniu. Można poczekać do jednego roku przed zaktualizowaniem do nowszej wersji, a można też pominąć aktualizacja do zainstalowania najnowszej dostępnej wersji. Ponieważ każda wersja jest zbiorczą, jeśli pominąć aktualizacji i zainstaluj najnowszą wersję, nadal uzyskasz dostęp do wszystkich funkcji i ulepszeń z poprzednich wersji.

Aby uzyskać więcej informacji, zobacz [pomocy technicznej dla wersji Current Branch](/sccm/core/servers/manage/current-branch-versions-supported).

**Opcje aktualizacji**
- Z active Software Assurance można zainstalować aktualizacji w konsoli dla wersji Current Branch.  
- Nie jest dostępna opcja przekonwertować bieżącej gałęzi do wersji Technical Preview. Wersji zapoznawczych Technical Preview są oddzielnych instalacji, które nie wymagają licencji.
- Nie jest dostępna opcja przekonwertować bieżącej gałęzi do długoterminowe Servicing Branch (LTSB). Należy odinstalować bieżącej gałęzi i następnie zainstalować LTSB jako nową instalację.

##  <a name="long-term-servicing-branch-of-system-center-configuration"></a>Długoterminowe gałęzi obsługi konfiguracji programu System Center
Jest to licencjonowane gałęzi do użycia w produkcji dla klientów programu Configuration Manager, którzy korzystają z bieżącej gałęzi i których wartość Zezwalaj ich Configuration Manager Software Assurance (SA) lub prawa równoważne subskrypcji wygaśnie po 1 października 2016 r. Aby uzyskać więcej informacji o Software Assurance i opcje licencjonowania, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](learn-more-editions.md).

LTSB jest oparty na wersji 1606. Tej gałęzi nie otrzymywać aktualizacje w konsoli, które dostarczania nowych funkcji lub aktualizowanie istniejących możliwości. Jednak podano krytycznych poprawek. Aby zainstalować LTSB, należy użyć wersji 1606 [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) występujący jako dysk DVD z programu System Center 2016 lub System Center Configuration Manager.

Aby zainstalować LTSB jako nową lokację lub uaktualnienie z obsługiwanej lokacji programu Configuration Manager 2012, należy użyć wersji 1606 [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) występujący jako dysk DVD z programu System Center 2016 lub wersji System Center Configuration Manager (Current Branch i długoterminowe obsługi gałęzi 1606). Nośnika linii bazowej można użyć do zainstalowania nowej lokacji, na którym działa wersja 1606 bieżącej gałęzi lub nowej lokacji z uruchomionym programem gałęzi obsługi długoterminowe.

> [!TIP]  
> Aby dowiedzieć się więcej na temat programu System Center 2016, zobacz [dokumentacji programu System Center 2016](https://technet.microsoft.com/system-center-docs/system-center). Ta dokumentacja identyfikuje również jak uzyskać programu System Center 2016, co wymaga umowy licencyjnej firmy Microsoft lub podobne prawa.

> Aby znaleźć System Center Configuration Manager w wersji 1606 w wolumin licencjonowania Service Center (VLSC), przejdź do **pliki do pobrania i klucze** karcie [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), wyszukaj "system center konfiguracji", a następnie wybierz **System Center Config Mgr (bieżącej gałęzi i LTSB)**.

> Można również uzyskać wersję ewaluacyjną programu System Center 2016 z [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview).

**Funkcje LTSB**
-    Odbiera aktualizacje w konsoli, dostarczających krytycznych poprawek
- Udostępnia opcję instalacji po wygasły Twoje umowy lub równoważne uprawnienia SA do programu Configuration Manager
- Program obsługuje uaktualnienie (konwersji) bieżącej gałęzi, jeśli masz bieżącej umowy SA lub odpowiednie prawa dostępu do programu Configuration Manager

**Ograniczenia**  
LTSB jest oparty na wersji Current Branch 1606 i ma następujące ograniczenia:
- LTSB nie jest obsługiwane 10 lat krytyczne aktualizacje zabezpieczeń po jej udostępnieniu wersji ogólnodostępnej (października 2016), po których, pomocy technicznej dla tej gałęzi wygaśnie. Aby uzyskać więcej informacji na temat cyklu pomocy technicznej, zobacz [Microsoft Lifecycle Policy](https://support.microsoft.com/en-us/lifecycle).
- Obsługuje ograniczony zestaw listę systemów operacyjnych serwera i klienta i powiązanych technologii, takich jak wersji programu SQL Server. Aby uzyskać więcej informacji o to, co jest obsługiwane w tej gałęzi, zobacz [obsługiwane konfiguracje dla gałęzi obsługi długoterminowe](supported-configurations-for-ltsb.md).
- Nie otrzymywać aktualizacje dla nowych funkcji.
- Nie obsługuje dodawania subskrypcji usługi Microsoft Intune, co uniemożliwia używanie:
  -    Usługa Intune w konfiguracji hybrydowego zarządzania urządzeniami Przenośnymi
 - Lokalne zarządzanie urządzeniami Przenośnymi
-    Nie obsługuje użycia nawigacyjnym obsługi systemu Windows 10, obsługi planów, Windows 10 Current Branch (CB) lub Current Branch for Business (CBB).
- Nieobsługiwana w przyszłych wydaniach systemu Windows 10 LTSB i Windows Server.
-    Brak obsługi analizy zasobów.
-    Brak obsługi dla punktów dystrybucji w chmurze.
-    Brak obsługi pomocy technicznej dla usługi Exchange Online jako łącznik programu Exchange.
-    Nie obsługuje żadnych funkcji wersji wstępnej.



**Opcje aktualizacji**
- Możesz przekonwertować instalacji LTSB do instalacji Current Branch. Konwersja do bieżącej gałęzi jest obsługiwana przed lub po pomocy technicznej dla LTSB wygaśnie.

  Aby dokonać konwersji, musi mieć aktywne umowy Software Assurance z firmą Microsoft. Aby uzyskać więcej informacji zobacz następujące linki:
  - [Uaktualnienie wersji Long-Term Servicing Branch do wersji Current Branch](convert-to-current-branch.md)
  - [Licencjonowanie i gałęzi programu System Center Configuration Manager](learn-more-editions.md)
  - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#baseline-and-update-versions) w [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates)
- Nie jest dostępna opcja Aby przekonwertować LTSB Technical Preview. Wersji zapoznawczych Technical Preview są oddzielnych instalacji, które nie wymagają licencji.
-    Nie można uaktualnić wersję ewaluacyjną bieżącej gałęzi do instalacji LTSB.


## <a name="technical-preview-for-system-center-configuration-manager"></a>Wersja zapoznawcza Technical Preview programu System Center Configuration Manager
Technical Preview jest przeznaczona do użytku w środowisku laboratoryjnym, w której chcesz poznać i wypróbować najnowsze funkcje opracowywanych dla programu Configuration Manager. Technical Preview nie jest obsługiwana w środowisku produkcyjnym i nie wymaga posiadania Software Assurance umowy licencyjnej.

Aby zainstalować nowych lokacji z uruchomionym programem Technical Preview, użyj najnowszej [nośnika linii bazowej dla programu System Center Configuration Manager Technical Preview](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview). Po zainstalowaniu wersji zapoznawczej Technical Preview, nowe wersje są dostępne jako aktualizacje w konsoli dla każdego miesiąca.

**Funkcje wersji zapoznawczej Technical Preview**
-  Oparte na nowe wersje linii bazowej bieżącej gałęzi
-  Odbiera aktualizacje w konsoli aktualizacji instalacji do najnowszej wersji Technical Preview
-  Zawiera nowe funkcje, które są opracowywane i dla którego chcesz naszych deweloperzy swoją opinię
-  Odbiera aktualizacje, które mają zastosowanie tylko do gałęzi Technical Preview

**Ograniczenia**
-  [Obsługa jest ograniczona](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview), łącznie z tylko jedną lokację główną, jak i do 10 klientów.  
-  Nie można uaktualnić do bieżącej gałęzi lub LTSB.
-  Nie obsługuje importowania lub eksportowania danych do innej instalacji programu Configuration Manager za pomocą migracji.
-  Nie obsługuje uaktualnienia poprzedniej wersji programu Configuration Manager.
-  Nie obsługuje instalacji w wersji ewaluacyjnej.

Funkcje, które zostały po raz pierwszy wprowadzone w wersji Technical Preview często są dodawane do bieżącej gałęzi w późniejszym aktualizacji. Każda nowa wersja Technical Preview zawiera funkcje z poprzednich wersji zapoznawczych technical Preview, nawet po te funkcje zostały dodane do bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).

**Opcje aktualizacji**
-    Można zainstalować aktualizację w konsoli dla nowej wersji Technical Preview.
-    Nie jest dostępna opcja konwersji wersji Technical Preview na bieżącej gałęzi lub LTSB.


## <a name="identify-your-branch-and-version"></a>Identyfikowanie gałęzi i wersji programu
Możesz wyświetlić informacje o wersji dla lokacji programu Configuration Manager, można również upewnić gałęzi.

**Wersja**   
Aby sprawdzić wersję lokacji, w konsoli przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli gdzie **wersja lokacji** pojawi się. Zobacz [ ]() listę wersji lokacji.

**Gałęzi**  
Aby potwierdzić gałąź witryny (jako LTSB lub Current Branch), w konsoli przejdź do **administracji** > **konfiguracja lokacji** > **witryny**i Otwórz **ustawienia hierarchii**. Jeśli ma tej opcji można przekonwertować na bieżącej gałęzi i jest aktywna, w lokacji działa wersja LTSB. Gdy w lokacji działa bieżącej gałęzi, ta opcja jest wyszarzony.
Aby uzyskać informacje o różnych wersji programu Configuration Manager, zobacz "wersje linii bazowej i aktualizacji" w [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates).

