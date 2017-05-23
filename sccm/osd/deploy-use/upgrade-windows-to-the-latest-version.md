---
title: Uaktualnij do najnowszej wersji systemu Windows | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak używać programu Configuration Manager do uaktualnienia systemu operacyjnego Windows 7 lub nowszej, aby system Windows 10."
ms.custom: na
ms.date: 02/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 288a4c649f371d9701fe7249449356aa222bf372
ms.openlocfilehash: 35f04e237efffbdb12893f658950a99dc0b98b85
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera opis czynności w System Center Configuration Manager do uaktualnienia systemu operacyjnego na komputerze z systemem Windows 7 lub nowszej, aby system Windows 10. Dostępne są różne metody wdrażania, takie jak wdrażanie przy użyciu nośników autonomicznych lub przy użyciu Centrum oprogramowania. Scenariusz uaktualnienia w miejscu do systemu Windows 10:  

-   Uaktualnia system operacyjny na komputerach z systemem operacyjnym Windows 7, Windows 8 lub Windows 8.1. Umożliwia również wykonywanie uaktualnień kompilacji do kompilacji w przypadku systemu Windows 10. Na przykład możesz uaktualnić system Windows 10 RTM do systemu Windows 10 w wersji 1511.  

-   Zachowuje aplikacje, ustawienia i dane użytkowników komputera.  

-   Nie ma zależności zewnętrznych, takich jak zestaw Windows ADK.  

-   Jest zwykle szybsze i bardziej odporne niż tradycyjne wdrażanie systemu operacyjnego.  

 Następujące sekcje zawierają informacje dotyczące wdrażania systemów operacyjnych za pośrednictwem sieci przy użyciu sekwencji zadań.  

##  <a name="BKMK_Plan"></a> Planowanieowanie  

-   **Sprawdzanie ograniczeń dotyczących sekwencji zadań uaktualniającej system operacyjny**  

     Sprawdź następujące wymagania i ograniczenia dotyczące sekwencji zadań uaktualniające system operacyjny, aby upewnić się, że spełnia Twoje potrzeby:  

    -   Należy dodawać tylko kroki sekwencji zadań powiązane z podstawowym zadaniem wdrażania systemów operacyjnych i konfigurowania komputerów po zainstalowaniu obrazu. Dotyczy to również kroków instalujących pakiety, aplikacje lub aktualizacje, a także kroków uruchamiających wiersze polecenia lub program PowerShell albo ustawiających zmienne dynamiczne.  

    -   Zanim zostanie wdrożona sekwencja zadań uaktualniania, zapoznaj się ze sterownikami i aplikacjami zainstalowanymi na komputerach, aby upewnić się, że są zgodne z systemem Windows 10.  

    -   Poniższe zadania nie są zgodne z uaktualnianiem w miejscu i wymagają użycia tradycyjnego wdrażania systemu operacyjnego:  

        -   Zmienianie przynależności do domeny komputerów lub aktualizowanie lokalnych administratorów.  

        -   Dokonywanie gruntownych zmian na komputerze, w tym zmian dotyczących partycji dysków, zmiany z systemu x86 na x64, wdrożenia interfejs UEFI lub zmiany podstawowego języka systemu operacyjnego.  

        -   Masz przy użyciu niestandardowego obrazu podstawowego, w tym wymagania niestandardowe przy użyciu 3<sup>usług pulpitu zdalnego</sup> strony szyfrowania dysku lub wymagają WinPE działania trybu offline.  

-   **Planowanie i implementowanie wymagań dotyczących infrastruktury**  

     Jedynym wymaganiem wstępnym dotyczącym scenariusza uaktualniania jest dostępność punktu dystrybucji dla pakietu uaktualniania systemu operacyjnego i innych pakietów uwzględnionych w sekwencji zadań. Aby uzyskać więcej informacji, zobacz [zainstalować lub zmodyfikować punkt dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

##  <a name="BKMK_Configure"></a> Konfiguracja  

1.  **Przygotowywanie pakietu uaktualnienia systemu operacyjnego**  

     Pakiet uaktualnienia systemu Windows 10 zawiera pliki źródłowe niezbędne do uaktualnienia systemu operacyjnego na komputerze docelowym. Ten pakiet uaktualnienia musi mieć taką samą wersję, architekturę i język jak uaktualniani klienci.  Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami uaktualnienia systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md).  

2.  **Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego**  

     Wykonaj kroki w [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md) zautomatyzować uaktualnienia systemu operacyjnego.  

    > [WAŻNE] Korzystając z nośników autonomicznych, musi zawierać obrazu rozruchowego w sekwencji zadań powinien być dostępny w Kreatorze nośnika sekwencji zadań.


    > [!NOTE]  
    >  Zazwyczaj użyjesz etapami [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md) Aby utworzyć sekwencję zadań, aby uaktualnić system operacyjny do systemu Windows 10. Sekwencja zadań zawiera krok uaktualniania systemu operacyjnego, a także dodatkowe zalecane kroki i grupy, aby obsłużyć end-to-end procesu uaktualniania. Jednakże, należy utworzyć niestandardową sekwencję zadań i dodać [uaktualnienia systemu operacyjnego](../understand/task-sequence-steps.md#BKMK_UpgradeOS) sekwencji zadań w celu uaktualnienia systemu operacyjnego. Jest to jedyny krok wymagany do uaktualnienia systemu operacyjnego do systemu Windows 10. Jeśli zostanie wybrana ta metoda również dodać [Uruchom ponownie komputer](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer) krok po kroku uaktualnienia systemu operacyjnego do przeprowadzenia uaktualnienia. Należy użyć **aktualnie zainstalowany domyślny system operacyjny** ustawienie, aby ponownie uruchomić komputer z zainstalowanym systemem operacyjnym i nie środowiska Windows PE.  

##  <a name="BKMK_Deploy"></a> Wdróż  

-   Użyj jednej z poniższych metod wdrażania, aby wdrożyć system operacyjny:  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci za pomocą Centrum oprogramowania](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [Do wdrażania systemu Windows bez użycia sieci należy używać nośników samodzielnych](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **Monitorowanie wdrożenia sekwencji zadań**  

     Aby monitorować wdrożenia sekwencji zadań, aby uaktualnić system operacyjny, zobacz [monitorowania wdrożeń systemu operacyjnego](monitor-operating-system-deployments.md).  

