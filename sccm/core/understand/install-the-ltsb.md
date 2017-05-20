---
title: "Instalacja lokacji za pomocą nośnika linii bazowej 1606 | Dokumentacja firmy Microsoft"
description: "Zainstalować lub uaktualnić LTSB dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/01/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4f9a5fd-f573-4b99-ad93-b2c76812e922
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 39653604ba5fd8e1fe9dd4d42889221d983f9bec
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="install-and-upgrade-with-the-version-1606-baseline-media-for-system-center-configuration-manager"></a>Instalowanie i uaktualnianie z wersji 1606 linii bazowej nośnika dla programu System Center Configuration Manager

*Dotyczy:  System Center Configuration Manager (bieżącej gałęzi) (długoterminowej obsługi oddziału)*

Po uruchomieniu Instalatora z nośnika linii bazowej 1606 wersji dla programu Configuration Manager, można zainstalować gałęzi obsługi długoterminowe lub bieżącej lokacji gałęzi programu System Center Configuration Manager.

Nośnik linii bazowej jest dostępna na dysku DVD w ramach programu Microsoft System Center 2016 lub wersji z System Center Configuration Manager (bieżącej gałęzi i długoterminowe obsługi gałęzi 1606). Aby dowiedzieć się więcej o nośnikach linii bazowej, zobacz [linii bazowej i aktualizacji wersji](/sccm/core/servers/manage/updates#baseline-and-udpate-versions).


Używając nośnika linii bazowej 1606 wersji jest lokacji instalacji lub uaktualnienia do:
- A *lokacji bieżącej gałęzi* oznacza to odpowiednik do lokacji, która została pierwszy zainstalowanych przy użyciu nośnika linii bazowej 1511, a następnie zaktualizować ją do wersji 1606 plus 1606 pakiet poprawek - KB3186654.
-    *LTSB witryny* oznacza to równoważna lokacji bieżącej gałęzi, która uruchamia pakiet poprawek wersji 1606 plus 1606 - KB3186654. Nośnik linii bazowej już zawiera pakiet poprawek.  Ale LTSB nie obsługuje wszystkie funkcje i możliwości dostępne w bieżącej gałęzi, jak określono w [wprowadzenie do długoterminowej obsługi gałęzi programu System Center Configuration Manager](introduction-to-the-ltsb.md).

Jeśli nie jesteś zaznajomiony z różnych oddziałów programu System Center Configuration Manager, zobacz [która gałąź programu Configuration Manager należy używać](which-branch-should-i-use.md).




## <a name="changes-to-setup-with-the-1606-baseline-media"></a>Zmiany dotyczące instalacji z nośnika 1606 linii bazowej
Nośnik linii bazowej 1606 wprowadza następujące zmiany do Instalatora programu Configuration Manager.

### <a name="branch-and-edition"></a>Tworzyć gałęzie i wersji
Po uruchomieniu Instalatora są teraz udostępniana strony licencjonowania, którym można wybrać gałęzi programu Configuration Manager ma być zainstalowany. Można wybrać bieżącej gałęzi lub LTSB jako licencjonowanej wersji instalacyjnej, lub wybrać wersji ewaluacyjnej programu bieżącej gałęzi w trybie instalacji bez licencji.

Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](learn-more-editions.md).

### <a name="software-assurance-expiration"></a>Software Assurance wygaśnięcia
Podczas instalacji, istnieje możliwość wprowadzenia **Data wygaśnięcia Software Assurance** wartość. Jest to opcjonalna wartość, która można określić jako wygodny monitu.

> [!NOTE]
> Firma Microsoft nie obsługuje sprawdzania datę wygaśnięcia, wprowadź i nie używa tej daty w celu weryfikacji licencji.  W takim przypadku go użyć jako przypomnienie od daty wygaśnięcia. Jest to przydatne, ponieważ programu Configuration Manager okresowo sprawdza, czy nowe aktualizacje oprogramowania oferowanych online, a stan licencji oprogramowania assurance powinna być bieżącym Aby kwalifikować się do korzystania z tych dodatkowych aktualizacji.    

- Można określić wartość daty na **klucz produktu** Kreatora instalacji po uruchomieniu Instalatora w wersji programu System Center Configuration Manager 1606 nośnika linii bazowej.
- Można również określić ta data, wybierając **właściwości ustawienia hierarchii** > **licencjonowania** w konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz "Software Assurance umowy" w [licencjonowania i gałęzie dla programu System Center Configuration Manager](learn-more-editions.md).


### <a name="additional-pre-upgrade-configurations"></a>Dodatkowe konfiguracje przed uaktualnieniem
Przed rozpoczęciem uaktualniania programu System Center 2012 Configuration Manager do LTSB, należy wykonać dodatkowe kroki w ramach Lista kontrolna uaktualniania wstępnego.  
Odinstaluj ról systemu lokacji, które nie obsługują LTSB:
- Punkt synchronizacji analizy zasobów
- Łącznik usługi Microsoft Intune
- Chmurowe punkty dystrybucji

Aby uzyskać więcej informacji, zobacz [uaktualnienia programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).


### <a name="new-scripted-installation-options"></a>Nowe opcje instalacji inicjowanych przez skrypty
Nośnika linii bazowej 1606 wersja obsługuje nowy klucz pliku skryptu instalacji nienadzorowanej instalacji inicjowanych przez skrypty nowej lokacji najwyższego poziomu. Dotyczy to instalowania nowego autonomicznej lokacji głównej lub Dodawanie witryny Administracja centralna w ramach scenariusza rozszerzania lokacji.

Zainstaluj licencjonowaną gałęzi za pomocą skryptu instalacji nienadzorowanej, należy dodać następujące części, nazw kluczy i wartości do sekcji Opcje skryptu. Nie trzeba używać tych wartości do skryptu instalacji wersji ewaluacyjnej programu bieżącej gałęzi:  

 **SABranchOptions**
-     **Nazwa klucza: SAActive**
  - Wartości: 0 lub 1.  
  - Szczegóły:  wersji ewaluacyjnej-licencjonowane bieżącej gałęzi instaluje 0 i 1 instaluje licencjonowaną wersję.   

- **CurrentBranch**
  - Wartości: 0 lub 1.  
  - Szczegóły:  Gałąź obsługi długoterminowe instaluje 0 i 1 instaluje bieżącej gałęzi.  

Na przykład aby zainstalować licencjonowaną wersję bieżącej gałęzi należy użyć:

  **Nazwa klucza: SABranchOptions**
   -    **SAActive = 1**
   - **CurrentBranch = 1**


> [!IMPORTANT]  
> **SABranchOptions** działa tylko w przypadku instalacji z nośnika linii bazowej. Nie ma zastosowania podczas uruchamiania Instalatora z dysku CD. Najnowsze folderu witryny sieci wcześniej zainstalowano za pomocą wersji 1606 nośnika linii bazowej.
>
> **SABranchOptions** nie ma zastosowania do uaktualnienia inicjowanych przez skrypty programu System Center 2012 Configuration Manager i zawsze powoduje w bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [użyć wiersza polecenia do zainstalowania lokacji programu System Center Configuration Manager](/sccm/core/servers/deploy/install/use-a-command-line-to-install-sites).


## <a name="install-a-new-site"></a>Zainstalować nową lokację
Używanie 1606 linii bazowej nośnika, aby zainstalować nową lokację z jednej gałęzi, użyj witryny planowania, przygotowania, i opisano procedury instalacji w [witryn Instalowanie programu System Center Configuration Manager](/sccm/core/servers/deploy/install/installing-sites) tematu z dodatkiem następujące zagadnienia dotyczące konfiguracji:

- Podczas instalacji należy wybrać gałęzi Menedżera konfiguracji, który chcesz zainstalować, i można określić szczegóły umowy Software Assurance.
- Wszystkie lokacje w tej samej hierarchii, należy uruchomić tego samego gałęzi. Mają hierarchię o różnych LTSB i bieżącej gałęzi w różnych lokacjach nie jest obsługiwane.
-    Nowa instalacja inicjowanych przez skrypty. Aby uzyskać więcej informacji, zobacz "New inicjowanych przez skrypty opcji instalacji" w tym artykule.

## <a name="expand-a-stand-alone-primary-site"></a>Rozszerzanie autonomicznej lokacji głównej
Po rozwinięciu autonomicznej lokacji głównej, który uruchamia LTSB.  Proces nie różni się od używanego dla bieżącego oddziale z jedno zastrzeżenie::

- Podczas instalowania nowej centralnej lokacji administracyjnej należy użyć Instalatora z oryginalnego nośnika źródłowego użytego do zainstalowania lokacji LTSB. Instalator jest uruchamiany z dysku CD. Najnowsze folderu, w tym scenariuszu nie jest obsługiwane.

Aby uzyskać więcej informacji o rozszerzaniu lokacji, zobacz "Rozszerzyć autonomiczną lokację główną" w [instalacji lokacji przy użyciu Kreatora instalacji](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).

## <a name="upgrade-from-system-center-2012-configuration-manager"></a>Uaktualnianie programu System Center 2012 Configuration Manager
Podczas uaktualniania programu System Center 2012 Configuration Manager, użyj witryny planowania i przygotowania oraz procedury opisane w [uaktualnienia programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager) tematu, ale bez następujące zmiany:

**Uaktualnienie do wersji bieżącej gałęzi:**
- Podczas instalacji należy wybrać bieżącej gałęzi i można określić szczegóły umowy Software Assurance.
-     Nowa instalacja inicjowanych przez skrypty. Aby uzyskać więcej informacji, zobacz "New inicjowanych przez skrypty opcji instalacji" w tym artykule.

**Uaktualnianie do LTSB:**  
- Dodatkowe kroki w celu następujące czynności na liście kontrolnej przed uaktualnieniem.
- Podczas instalacji należy wybrać LTSB i szczegóły można określić dla umowie Software Assurance.
- Można uaktualnić tylko z lokacją uruchomioną System Center 2012 Configuration Manager z dodatkiem Service Pack 2 lub System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1.

### <a name="in-place-upgrade-paths-for-the-1606-baseline-media"></a>Ścieżki uaktualniania dla nośnika linii bazowej 1606 w miejscu
Nośnik linii bazowej 1606 służą do uaktualnienia następujące do licencjonowanej wersji programu System Center Configuration Manager:
- System Center 2012 Configuration Manager z dodatkiem Service Pack 2.
- System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1.

Umożliwia także ten nośnik do uaktualnienia wersji ewaluacyjnej-licencjonowane bieżącej gałęzi do w pełni licencjonowaną wersję bieżącej gałęzi.

Ten nośnik nie obsługuje uaktualnienia:
- Inne wersje programu System Center 2012 Configuration Manager.
- Menedżer konfiguracji 2007 lub starszym.
- Release candidate instalację programu System Center Configuration Manager.

## <a name="about-the-cdlatest-folder-and-the-ltsb"></a>O dysku CD. Folder najnowsze i LTSB
Poniżej wymieniono ograniczenia dotyczące używania programu Configuration Manager tworzy na dysku CD z nośnika. Najnowszy folder na serwerze lokacji. Te limity mają zastosowanie do lokacji z systemem LTSB:

Nośnik na dysku CD. Najnowsze folderu jest obsługiwane:
- Odzyskiwanie witryny.
- Obsługa lokacji.
- Instalowanie dodatkowych podrzędnych lokacji głównych.

Nośnik na dysku CD. Najnowszy folder nie jest obsługiwana dla:  
- Instalowanie centralnej lokacji administracyjnej w ramach scenariusza rozszerzania lokacji.

Aby uzyskać więcej informacji, zobacz [dysku CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder).

## <a name="backup-recovery-and-site-maintenance-for-the-ltsb"></a>Kopia zapasowa, odzyskiwanie i obsługa lokacji LTSB
Tworzenie kopii zapasowych, odzyskanie lub Uruchom konserwację lokacji w lokacji, która uruchamia LTSB, użyj wskazówki i procedury z [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

Użyj Menedżera konfiguracji Instalatora z dysku CD. Folder najnowszej kopii zapasowej witryny LTSB.

