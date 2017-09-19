---
title: Uaktualnianie do najnowszej wersji systemu Windows | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak używać programu Configuration Manager do uaktualnienia systemu operacyjnego z systemu Windows 7 lub nowszym do systemu Windows 10."
ms.custom: na
ms.date: 02/06/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c21eec87-ad1c-4465-8e45-5feb60b92707
caps.latest.revision: "13"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 412c2c644cc7f17f307c02b84471f3ee494045ec
ms.sourcegitcommit: 31c670a4bce74fd64a7d46ebf7702f65b80d4147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2017
---
# <a name="upgrade-windows-to-the-latest-version-with-system-center-configuration-manager"></a>Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera opis czynności w System Center Configuration Manager do uaktualnienia systemu operacyjnego na komputerze z systemem Windows 7 lub nowszym do systemu Windows 10 lub Windows Server 2012 do systemu Windows Server 2016 na komputerze docelowym. Dostępne są różne metody wdrażania, takie jak wdrażanie przy użyciu nośników autonomicznych lub przy użyciu Centrum oprogramowania. Scenariusz uaktualnienia w miejscu.  

-   Uaktualnia system operacyjny na komputerach z systemem operacyjnym:
    - Windows 7, Windows 8 lub Windows 8.1. Umożliwia również wykonywanie uaktualnień kompilacji do kompilacji w przypadku systemu Windows 10. Na przykład możesz uaktualnić system Windows 10 RTM do systemu Windows 10 w wersji 1511.  
    - Windows Server 2012. Można także utworzyć uaktualnień kompilacji do kompilacji systemu Windows Server 2016. Aby uzyskać szczegółowe informacje na temat obsługiwanych ścieżek uaktualniania, zobacz [obsługiwane ścieżki uaktualniania](https://docs.microsoft.com/windows-server/get-started/supported-upgrade-paths#upgrading-previous-retail-versions-of-windows-server-to-windows-server-2016).    

-   Zachowuje aplikacje, ustawienia i dane użytkowników komputera.  

-   Nie ma zależności zewnętrznych, takich jak zestaw Windows ADK.  

-   Jest szybsze i bardziej odporne niż tradycyjne wdrażanie systemu operacyjnego.  

 Następujące sekcje zawierają informacje dotyczące wdrażania systemów operacyjnych za pośrednictwem sieci przy użyciu sekwencji zadań.  

##  <a name="BKMK_Plan"></a> Planowanieowanie  

-   **Sprawdzanie ograniczeń dotyczących sekwencji zadań uaktualniającej system operacyjny**  

     Sprawdź następujące wymagania i ograniczenia dotyczące sekwencji zadań uaktualniające system operacyjny, aby upewnić się, że spełnia Twoje potrzeby:  

    -   Należy dodawać tylko kroki sekwencji zadań powiązane z podstawowym zadaniem wdrażania systemów operacyjnych i konfigurowania komputerów po zainstalowaniu obrazu. Dotyczy to również kroków instalujących pakiety, aplikacje lub aktualizacje, a także kroków uruchamiających wiersze polecenia lub program PowerShell albo ustawiających zmienne dynamiczne.  

    -   Zanim zostanie wdrożona sekwencja zadań uaktualniania, zapoznaj się ze sterownikami i aplikacjami zainstalowanymi na komputerach, aby upewnić się, że są zgodne z systemem Windows 10.  

    -   Poniższe zadania nie są zgodne z uaktualnianiem w miejscu i wymagają użycia tradycyjnego wdrażania systemu operacyjnego:  

        -   Zmienianie przynależności do domeny komputerów lub aktualizowanie lokalnych administratorów.  

        -   Dokonywanie gruntownych zmian na komputerze, w tym zmian dotyczących partycji dysków, zmiany z systemu x86 na x64, wdrożenia interfejs UEFI lub zmiany podstawowego języka systemu operacyjnego.  

        -   Masz własne wymagania dotyczące użycia niestandardowego obrazu podstawowego, za pomocą 3<sup>usług pulpitu zdalnego</sup> strony szyfrowanie dysków lub wymagają środowiska WinPE w trybie offline.  

-   **Planowanie i implementowanie wymagań dotyczących infrastruktury**  

     Jedynym wymaganiem wstępnym dotyczącym scenariusza uaktualniania jest, że punkt dystrybucji dla pakietu uaktualnienia systemu operacyjnego i inne pakiety, które obejmują w sekwencji zadań. Aby uzyskać więcej informacji, zobacz [zainstalować lub zmodyfikować punkt dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

##  <a name="BKMK_Configure"></a> Konfiguracja  

1.  **Przygotowywanie pakietu uaktualnienia systemu operacyjnego**  

     Pakiet uaktualnienia systemu Windows 10 zawiera pliki źródłowe niezbędne do uaktualnienia systemu operacyjnego na komputerze docelowym. Pakiet uaktualnienia musi być edition, architekturę i język, klientów, którzy uaktualniania.  Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami uaktualnień systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md).  

2.  **Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego**  

     Wykonaj kroki w [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md) Aby zautomatyzować uaktualnianie systemu operacyjnego.  

    > [!IMPORTANT]
    > Korzystając z nośników autonomicznych, musi zawierać obraz rozruchowy w sekwencji zadań dla powinna być dostępna w Kreatorze nośnika sekwencji zadań.

    > [!NOTE]  
    > Zwykle Użyj kroków w [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md) do tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego do systemu Windows 10. Sekwencja zadań zawiera krok uaktualniania systemu operacyjnego, a także dodatkowe zalecane kroki i grupy służące do obsługi end-to-end procesu uaktualniania. Można jednak utworzyć niestandardową sekwencję zadań i dodać [Uaktualnij System operacyjny](../understand/task-sequence-steps.md#BKMK_UpgradeOS) krok sekwencji zadań w celu uaktualnienia systemu operacyjnego. Jest to jedyny krok wymagany do uaktualnienia systemu operacyjnego do systemu Windows 10. W przypadku wybrania tej metody, również dodać [Uruchom ponownie komputer](../understand/task-sequence-steps.md#BKMK_RestartComputer) krok po kroku uaktualniania systemu operacyjnego w celu ukończenia uaktualniania. Należy użyć **aktualnie zainstalowany domyślny system operacyjny** ustawienie, aby ponownie uruchomić komputer w zainstalowanego systemu operacyjnego i nie środowiska Preinstalacyjnego systemu Windows.  

##  <a name="BKMK_Deploy"></a> Wdróż  

-   Użyj jednej z poniższych metod wdrażania, aby wdrożyć system operacyjny:  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu programu Software Center](use-software-center-to-deploy-windows-over-the-network.md)  

    -   [Zastosowanie nośników samodzielnych do wdrażania systemu Windows bez użycia sieci](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **Monitorowanie wdrożenia sekwencji zadań**  

     Aby monitorować wdrożenia sekwencji zadań w celu uaktualnienia systemu operacyjnego, zobacz [monitorowanie wdrożeń systemu operacyjnego](monitor-operating-system-deployments.md).  
