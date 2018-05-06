---
title: Uaktualnienie do systemu Windows 10
titleSuffix: Configuration Manager
description: Dowiedz się, jak używać programu Configuration Manager do uaktualnienia systemu operacyjnego z systemu Windows 7 lub nowszym do systemu Windows 10.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fbba0306cececebeb7a0e20757e7de3b0d4d0e70
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera opis czynności w programie Configuration Manager do uaktualnienia systemu operacyjnego na komputerze. Dostępne są różne metody wdrażania, takie jak wdrażanie przy użyciu nośników autonomicznych lub przy użyciu Centrum oprogramowania. Scenariusz uaktualnienia w miejscu zawiera następujące funkcje:  

-   Uaktualnia system operacyjny na komputerach z systemem operacyjnym:
    - Windows 7, Windows 8 lub Windows 8.1. Umożliwia również wykonywanie uaktualnień kompilacji do kompilacji w przypadku systemu Windows 10. Na przykład systemu Windows 10 w wersji 1607 można uaktualnić do systemu Windows 10 w wersji 1709.  
    
    - Windows Server 2012. Można także utworzyć uaktualnień kompilacji do kompilacji systemu Windows Server 2016. Aby uzyskać więcej informacji na temat obsługiwanych ścieżek uaktualniania, zobacz [obsługiwane ścieżki uaktualniania](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016).    

-   Zachowuje aplikacje, ustawienia i dane użytkowników komputera.  

-   Nie ma zależności zewnętrznych, takich jak zestaw Windows ADK.  

-   Jest szybsze i bardziej odporne niż tradycyjne wdrażanie systemu operacyjnego.  


> [!Note]  
> Począwszy od wersji 1802 sekwencji zadań uaktualniania w miejscu systemu Windows 10 obsługuje wdrażanie na klientach internetowych zarządzanych za pomocą [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway). Dzięki tej możliwości użytkownicy zdalni łatwiej uaktualniania do systemu Windows 10, bez konieczności łączenia się z intranetem. Aby uzyskać więcej informacji, zobacz [uaktualnienia w miejscu wdrożenia systemu Windows 10 za pomocą CMG](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg). <!-- 1357149 -->



##  <a name="BKMK_Plan"></a> Planowanieowanie  

### <a name="task-sequence-requirements-and-limitations"></a>Wymagania dotyczące sekwencji zadań i ograniczenia

Przejrzyj poniższe wymagania i ograniczenia dotyczące sekwencji zadań w celu uaktualnienia systemu operacyjnego do upewnij się, że spełnia Twoje potrzeby:  

  -   Dodawać tylko kroki sekwencji zadań, które są powiązane z podstawowym zadaniem uaktualniania systemu operacyjnego. Kroki te obejmują głównie instalowanie pakiety, aplikacje lub aktualizacje. Użyj także kroków uruchamiających wiersze polecenia, programu PowerShell, lub albo ustawiających zmienne dynamiczne.  

  -   Zanim zostanie wdrożona sekwencja zadań uaktualniania, zapoznaj się ze sterownikami i aplikacjami zainstalowanymi na komputerach, aby upewnić się, że są zgodne z systemem Windows 10.  

  -   Następujące zadania nie są zgodne z uaktualnianiem w miejscu. One wymagają użycia tradycyjnego wdrażania systemu operacyjnego:  

     -   Zmiana członkostwa w domenie komputera, lub aktualizowanie lokalnej grupy administratorów.  

     -   Dokonywanie gruntownych zmian na komputerze, takich jak: 
         - Zmiana partycji dysku
         - Zmiana architektura systemu z x86 do x 64
         - Implementacja interfejsu UEFI. (Aby uzyskać więcej informacji na temat możliwych opcji, zobacz [Konwertowanie systemu BIOS na UEFI podczas uaktualniania w miejscu](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).)
         - Modyfikowanie języka podstawowego systemu operacyjnego  

     -   Masz własne wymagania dotyczące użycia niestandardowego obrazu podstawowego, za pomocą szyfrowania dysków innych firm lub wymagają środowiska WinPE w trybie offline.  

### <a name="infrastructure-requirements"></a>Wymagania dotyczące infrastruktury  

Jedynym wymaganiem wstępnym koniecznym do scenariusza uaktualniania jest dostępność punktu dystrybucji. Dystrybuuj pakiet uaktualnienia systemu operacyjnego i inne pakiety, które obejmują w sekwencji zadań. Aby uzyskać więcej informacji, zobacz [zainstalować lub zmodyfikować punkt dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).



##  <a name="BKMK_Configure"></a> Konfiguracja  

### <a name="prepare-the-os-upgrade-package"></a>Przygotowywanie pakietu uaktualnienia systemu operacyjnego  

  Pakiet uaktualnienia systemu Windows 10 zawiera pliki źródłowe niezbędne do uaktualnienia systemu operacyjnego na komputerze docelowym. Pakiet uaktualnienia musi być edition, architekturę i język, klientów, którzy uaktualniania. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami uaktualnień systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md).  


### <a name="create-a-task-sequence-to-upgrade-the-os"></a>Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego  

  Wykonaj kroki w [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md) Aby zautomatyzować uaktualnianie systemu operacyjnego.  

   > [!NOTE]  
   > Zwykle Użyj kroków w [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md) do tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego do systemu Windows 10. Sekwencja zadań zawiera krok uaktualniania systemu operacyjnego, a także dodatkowe zalecane kroki i grupy służące do obsługi end-to-end procesu uaktualniania. Można jednak utworzyć niestandardową sekwencję zadań i dodać [Uaktualnij System operacyjny](../understand/task-sequence-steps.md#BKMK_UpgradeOS) krok sekwencji zadań w celu uaktualnienia systemu operacyjnego. Ten krok jest tylko jeden wymagane do uaktualniania systemu operacyjnego do systemu Windows 10. W przypadku wybrania tej metody, również dodać [Uruchom ponownie komputer](../understand/task-sequence-steps.md#BKMK_RestartComputer) krok po kroku uaktualniania systemu operacyjnego w celu ukończenia uaktualniania. Należy użyć **aktualnie zainstalowany domyślny system operacyjny** ustawienie, aby ponownie uruchomić komputer do zainstalowanego systemu operacyjnego i nie środowiska Preinstalacyjnego systemu Windows.  



##  <a name="BKMK_Deploy"></a> Wdróż  

Aby wdrożyć system operacyjny, użyj jednej z następujących metod wdrażania:  

  -   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu programu Software Center](use-software-center-to-deploy-windows-over-the-network.md)  

  -   [Zastosowanie nośników samodzielnych do wdrażania systemu Windows bez użycia sieci](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

      > [!IMPORTANT]  
      > Korzystając z nośników autonomicznych, musi zawierać obraz rozruchowy w sekwencji zadań dla powinna być dostępna w Kreatorze nośnika sekwencji zadań.




## <a name="monitor"></a>Monitor  

Aby monitorować wdrożenia sekwencji zadań w celu uaktualnienia systemu operacyjnego, zobacz [monitorowanie wdrożeń systemu operacyjnego](monitor-operating-system-deployments.md).  
