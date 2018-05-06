---
title: Która gałąź należy używać
titleSuffix: Configuration Manager
description: Dowiedz się różnic między dostępne gałęzi programu System Center Configuration Manager.
ms.date: 05/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a3be4f8f-3d44-4e3c-9fa1-e85f30a36e72
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 258d8ac160e9ee31189f8771fd6109d1bb17f714
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="which-branch-of-configuration-manager-should-i-use"></a>Które gałęzi programu Configuration Manager należy użyć?

*Dotyczy: System Center Configuration Manager (Current Branch, długoterminowe gałęzi obsługi i Technical Preview)*


Dostępne są trzy gałęzie programu System Center Configuration Manager: bieżącej gałęzi, długoterminowe gałęzi obsługi i gałęzi wersji zapoznawczej technical preview. Użyj tego tematu, aby wybrać prawa gałęzi.

> [!TIP]  
> Wszystkie lokacje w hierarchii należy uruchomić na tym samym oddziale. Aby mieć hierarchii o różnych gałęziach w różnych lokacjach nie są obsługiwane.


## <a name="current-branch"></a>Bieżąca gałąź
Tej gałęzi jest licencjonowany do użycia w środowisku produkcyjnym. Użyj tej gałęzi, aby uzyskać najnowsze funkcje i funkcje. Jeśli masz następujące licencje, można użyć tej gałęzi:  
- Centrum danych programu System Center
- Standard programu System Center
- System Center Configuration Manager
- Prawa równoważne subskrypcji  

Aby uzyskać więcej informacji na temat Software Assurance i opcje licencjonowania, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](learn-more-editions.md) i [często zadawane pytania dotyczące gałęzi programu Configuration Manager i Licencjonowanie](/sccm/core/understand/product-and-licensing-faq).

Bieżąca gałąź jest aktualizowana kilka razy w roku z nowych funkcji. Każda wersja aktualizacji jest obsługiwana przez jeden rok po ich wydaniu. Aktualizacja do nowszej wersji current Branch na lub przed wygaśnięciem okresu rocznego. Aktualizacje do nowszych wersji są dostępne jako aktualizacje w konsoli.

Aby zainstalować bieżącej gałęzi jako nowej lokacji, należy użyć [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions). Nośnika linii bazowej należy również użyć do uaktualnienia programu System Center 2012 Configuration Manager z dodatkiem Service Pack 2 lub System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1. Dostęp do tego nośnika zależy od tego, jak organizacji licencję programu System Center Configuration Manager. 

Umożliwia także nośnika linii bazowej w celu zainstalowania nowej lokacji, który jest w wersji próbnej bieżącej gałęzi. Wersja ewaluacyjna nie wymagają licencji. Można użyć wersji ewaluacyjnej na okres 180 dni. Obsługuje ona uaktualnienia do wersji licencjonowanej bieżącej gałęzi. Aby zainstalować wersję ewaluacyjną, pobierz go z [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-configuration-manager-and-endpoint-protection).

>  [!NOTE]  
> Do zainstalowania lokacji dla nowej hierarchii programu Configuration Manager, należy użyć nośnika linii bazowej. Jeśli wcześniej zainstalowano wersji linii bazowej, należy użyć aktualizacji w konsoli, aby zaktualizować lokacji do nowej wersji.  
>  
> Lokacje, które są aktualizowane przy użyciu wynik aktualizacji w lokacji, które są takie same jak nowej lokacji zainstalowane za pomocą nośnika linii bazowej w konsoli.
>
> Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](/sccm/core/servers/manage/updates).  


### <a name="features-of-the-current-branch"></a>Funkcje bieżącej gałęzi
- Odbiera [aktualizacje w konsoli](/sccm/core/servers/manage/install-in-console-updates) który udostępnia nowe funkcje do użycia.
- Odbiera aktualizacje w konsoli, które dostarczać aktualizacje zabezpieczeń oraz poprawki jakości istniejących funkcji.
- Obsługuje aktualizacje poza pasmem, gdy jest to konieczne. Aby uzyskać więcej informacji, zobacz [używanie narzędzia rejestracji aktualizacji](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes) lub [przy użyciu instalatora poprawek](/sccm/core/servers/manage/use-the-hotfix-installer-to-install-updates).
- Integruje się w usłudze Microsoft Intune i innych usług w chmurze.
- Obsługuje [migracji danych](/sccm/core/migration/migrate-data-between-hierarchies) do i z innych instalacji programu Configuration Manager.
- Program obsługuje uaktualnienie z poprzednich wersji programu Configuration Manager.
- Obsługuje instalację w wersji ewaluacyjnej, z którego można później uaktualnić do w pełni licencjonowanej instalacji.

Początkowa wersja Current Branch był w wersji 1511. Kolejne aktualizacje obejmują 1606 wersji 1602 i tak dalej. Każda wersja pozostaje w pomocy technicznej przez jeden rok, i firma Microsoft zaleca aktualizacji do najnowszej wersji wkrótce po ich wydaniu. Można poczekać do jednego roku przed zaktualizowaniem do nowszej wersji, a można też pominąć aktualizacja do zainstalowania najnowszej dostępnej wersji. Ponieważ każda wersja jest zbiorczą, jeśli pominąć aktualizacji i zainstaluj najnowszą wersję, możesz nadal korzystać z wszystkich funkcji i ulepszeń z poprzednich wersji.

Aby uzyskać więcej informacji, zobacz [pomocy technicznej dla bieżącej wersji gałęzi](/sccm/core/servers/manage/current-branch-versions-supported).


### <a name="update-options"></a>Opcje aktualizacji
- Z active Software Assurance można zainstalować aktualizacji w konsoli dla bieżącej wersji gałęzi.  
- Nie jest dostępna opcja przekonwertować bieżącej gałęzi do gałęzi wersji zapoznawczej technical preview. Gałęzie wersji zapoznawczej Technical preview są oddzielnych instalacji, które nie wymagają licencji.
- Nie jest dostępna opcja przekonwertować bieżącej gałęzi do długoterminowego obsługi branch (LTSB). Należy odinstalować bieżącej gałęzi i następnie zainstalować LTSB jako nową instalację.



##  <a name="long-term-servicing-branch"></a>Długoterminowe obsługi gałęzi 
Tej gałęzi jest licencjonowany do użycia w produkcji dla klientów programu Configuration Manager, którzy korzystają z bieżącej gałęzi i których wartość Zezwalaj ich Configuration Manager Software Assurance (SA) lub prawa równoważne subskrypcji wygaśnie po 1 października 2016 r. Aby uzyskać więcej informacji o Software Assurance i opcje licencjonowania, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](learn-more-editions.md) i [— często zadawane pytania dla gałęzi programu Configuration Manager ilicencjonowania](/sccm/core/understand/product-and-licensing-faq).

LTSB jest oparty na wersji 1606. Tej gałęzi nie otrzymywać aktualizacje w konsoli, które dostarczania nowych funkcji lub aktualizowanie istniejących możliwości. Jednak podano krytycznych poprawek. Aby zainstalować LTSB, należy użyć wersji 1606 [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) której można korzystać z programu System Center 2016. Nowsze wersje linii bazowej nie obsługują instalacji LTSB.

Aby zainstalować LTSB jako nową lokację lub uaktualnienie z obsługiwanej lokacji programu Configuration Manager 2012, należy użyć wersji 1606 [nośnika linii bazowej](/sccm/core/servers/manage/updates#baseline-and-update-versions) której można korzystać z programu System Center 2016. Nośnika linii bazowej można użyć do zainstalowania nowej lokacji, na którym działa wersja 1606 bieżącej gałęzi lub nowej lokacji z uruchomionym programem długoterminowej gałęzi obsługi.

> [!TIP]  
> Aby dowiedzieć się więcej na temat programu System Center 2016, zobacz [dokumentacji programu System Center 2016](https://docs.microsoft.com/system-center/index). Ta dokumentacja identyfikuje również jak uzyskać programu System Center 2016, co wymaga umowy licencyjnej firmy Microsoft lub podobne prawa.  
>  
> Aby znaleźć System Center Configuration Manager w wersji 1606 w wolumin licencjonowania Service Center (VLSC), przejdź do **pliki do pobrania i klucze** karcie [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), wyszukaj `System Center 2016`, a następnie wybierz pozycję **Centrum danych do programu system Center 2016** lub **Standard programu System Center 2016**.  
>  
> Można również uzyskać wersję ewaluacyjną programu System Center 2016 z [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-system-center-technical-preview).  


### <a name="features-of-the-ltsb"></a>Funkcje LTSB
-   Odbiera aktualizacje w konsoli, dostarczających krytycznych poprawek.
- Zapewnia opcje instalacji, gdy wygasły Twoje umowy lub równoważne uprawnienia SA do programu Configuration Manager.
- Program obsługuje uaktualnienie (konwersji) bieżącej gałęzi, jeśli masz bieżącej umowy SA lub odpowiednie prawa dostępu do programu Configuration Manager.


### <a name="limitations"></a>Ograniczenia  
LTSB jest oparta na bieżącą wersję gałęzi 1606 i ma następujące ograniczenia:
- LTSB nie jest obsługiwane 10 lat krytyczne aktualizacje zabezpieczeń po jej udostępnieniu wersji ogólnodostępnej (października 2016), po których, pomocy technicznej dla tej gałęzi wygaśnie. Aby uzyskać więcej informacji na temat cyklu życia pomocy technicznej, zobacz [Microsoft Lifecycle Policy](https://support.microsoft.com/lifecycle).
- Obsługuje ograniczony zestaw listę systemów operacyjnych serwera i klienta i powiązanych technologii, takich jak wersji programu SQL Server. Aby uzyskać więcej informacji o to, co jest obsługiwane w tej gałęzi, zobacz [obsługiwane konfiguracje dla długoterminowego gałęzi obsługi](supported-configurations-for-ltsb.md).
- Nie odbiera aktualizacje dla nowych funkcji
- Nie obsługuje następujące możliwości: 
   - Dodawanie subskrypcję Microsoft Intune, co uniemożliwia używanie:
     -  Usługa Intune w konfiguracji hybrydowego zarządzania urządzeniami Przenośnymi
     - Lokalne zarządzanie urządzeniami Przenośnymi
   -    Windows 10 obsługi pulpitu nawigacyjnego, obsługi plany lub kanału półroczne systemu Windows 10
   - W przyszłych wydaniach systemu Windows 10 LTSB i Windows Server
   -    Analiza zasobów
   -    Chmurowe punkty dystrybucji
   -    Usługi Exchange Online jako łącznik programu Exchange
   -    Wszystkie funkcje wersji wstępnej


### <a name="update-options"></a>Opcje aktualizacji
- Możesz przekonwertować instalacji LTSB do instalacji current branch. Konwersja do bieżącej gałęzi jest obsługiwana przed lub po pomocy technicznej dla LTSB wygaśnie.

  Aby dokonać konwersji, musi mieć aktywne umowy Software Assurance z firmą Microsoft. Aby uzyskać więcej informacji zobacz następujące linki:
  - [Uaktualnienie wersji Long-Term Servicing Branch do wersji Current Branch](convert-to-current-branch.md)
  - [Licencjonowanie i gałęzi programu System Center Configuration Manager](learn-more-editions.md)
  - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#baseline-and-update-versions) 
- Nie jest dostępna opcja przekonwertować LTSB do gałęzi wersji zapoznawczej technical preview. Gałęzie wersji zapoznawczej Technical preview są oddzielnych instalacji, które nie wymagają licencji.
-   Nie można uaktualnić wersję ewaluacyjną bieżącej gałęzi do instalacji LTSB.



## <a name="technical-preview-branch"></a>Gałąź wersji zapoznawczej Technical preview
Gałąź wersji zapoznawczej technical preview jest przeznaczona do użytku w środowisku laboratoryjnym. Dowiedz się więcej o i wypróbować najnowsze funkcje opracowywanych dla programu Configuration Manager. Nie jest obsługiwany w środowisku produkcyjnym i nie wymaga posiadania Software Assurance umowy licencyjnej.

Aby zainstalować nowych lokacji z uruchomionym programem gałęzi wersji zapoznawczej technical preview, użyj najnowszej [nośnika linii bazowej dla gałęzi wersji zapoznawczej technical preview](/sccm/core/get-started/technical-preview#install-and-update-the-technical-preview). Po zainstalowaniu wersji zapoznawczej technical preview gałęzi nowe wersje są dostępne jako aktualizacje w konsoli dla każdego miesiąca.


### <a name="features-of-the-technical-preview-branch"></a>Funkcje wersji zapoznawczej technical preview gałęzi
-  Oparte na nowe wersje linii bazowej bieżącej gałęzi
-  Odbiera aktualizacje w konsoli aktualizacji instalacji do najnowszej wersji zapoznawczej technical preview w gałęzi
-  Zawiera nowe funkcje, które są opracowywane i dla których Microsoft chce swoją opinię
-  Odbiera aktualizacje, które mają zastosowanie tylko do gałęzi wersji zapoznawczej technical preview


### <a name="limitations"></a>Ograniczenia
-  [Obsługa jest ograniczona](/sccm/core/get-started/technical-preview#requirements-and-limitatins-for-the-techincal-preview), łącznie z tylko jedną lokację główną, jak i do 10 klientów.  
-  Nie można uaktualnić do bieżącej gałęzi lub LTSB.
-  Nie obsługuje następujące zachowania:
   - Za pomocą migracji do importowania lub eksportowania danych do innej instalacji programu Configuration Manager
   - Uaktualnianie z poprzedniej wersji programu Configuration Manager
   - Instalacja w wersji ewaluacyjnej

Funkcje, które wprowadzona w gałęzi wersji zapoznawczej technical preview często są dodawane do bieżącej gałęzi w późniejszym aktualizacji. Każda nowa wersja gałęzi wersji zapoznawczej technical preview zawiera funkcje z poprzedniej wersji zapoznawczej technical preview gałęzie, nawet po te funkcje zostały dodane do bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [Technical preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).


### <a name="update-options"></a>Opcje aktualizacji
-   Można zainstalować żadnych aktualizacji w konsoli dla nowej wersji gałęzi technical preview.
-   Nie jest dostępna opcja konwersji wersji zapoznawczej technical preview gałąź na bieżącej gałęzi lub LTSB.



## <a name="identify-your-version-and-branch"></a>Identyfikowanie gałęzi i wersji programu

### <a name="version"></a>Wersja   
Aby sprawdzić wersję lokacji, w konsoli przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli. Wyświetla to okno dialogowe **wersja lokacji**. Aby uzyskać listę wersji lokacji, zobacz [wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#bkmk_Baselines).

### <a name="branch"></a>Gałęzi
Aby potwierdzić gałąź witryny, w konsoli przejdź do **administracji** > **konfiguracja lokacji** > **witryny**i Otwórz **Ustawienia hierarchii**. Jeśli ma tej opcji można przekonwertować na bieżącej gałęzi i jest aktywna, w lokacji działa wersja LTSB. Gdy w lokacji działa bieżącej gałęzi, ta opcja jest wyszarzony.

Aby uzyskać więcej informacji o różnych wersji programu Configuration Manager, zobacz [wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#bkmk_Baselines).
