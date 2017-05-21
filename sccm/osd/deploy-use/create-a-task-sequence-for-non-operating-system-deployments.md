---
title: "Tworzenie sekwencji zadań dla wdrożeń systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Tworzenie sekwencji zadań, które nie są związane z wdrażaniem systemów operacyjnych, takich jak dystrybucji oprogramowania, aktualizacji sterowników, edytowanie stanu użytkownika, np."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: b4b04907f2cd48d81e864e46ca47c14a0b98a9f7
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-for-non-operating-system-deployments-with-system-center-configuration-manager"></a>Tworzenie sekwencji zadań dla wdrożeń systemu operacyjnego z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Sekwencje zadań w programie System Center Configuration Manager służą do automatyzowania różne zadania w danym środowisku. Te zadania zostały utworzone i przetestowane głównie pod kątem wdrażania systemów operacyjnych.  Configuration Manager ma wiele funkcji, które powinny być podstawowej stosowanej dla scenariuszy takich jak technologii [instalacji aplikacji](../../apps/understand/introduction-to-application-management.md), [instalacja aktualizacji oprogramowania](../../sum/understand/software-updates-introduction.md), [ustawienie konfiguracji](../../compliance/understand/ensure-device-compliance.md), lub niestandardowych automatyzacji. Istnieją inne technologie automatyzacji programu Microsoft System Center, takie jak [Orchestrator](https://technet.microsoft.com/library/hh237242.aspx) i [Automatyzacja zarządzania usługami](https://technet.microsoft.com/library/dn469260.aspx) , które również należy rozważyć.  

Power sekwencji zadań znajduje się w ich elastyczność i jak ich używać do konfigurowania ustawień klienta, dystrybucja oprogramowania, zaktualizować sterowniki, Edytuj stany użytkownika i wykonywać inne zadania, niezależnie od wdrożenia systemu operacyjnego. Można utworzyć niestandardową sekwencję zadań i dodać do niej dowolną liczbę zadań. Korzystanie z niestandardowych sekwencji zadań do wdrożenia systemu operacyjnego jest obsługiwany w programie Configuration Manager. Jednak jeśli wyniki sekwencji zadań w niepożądanych lub niespójne wyniki, Przyjrzyj się sposobów, aby uprościć operację. Można to zrobić za pomocą prostsze kroki dzielenia akcje między wieloma sekwencje zadań, lub wykonując etapowe podejścia do tworzenia i testowania sekwencji zadań.

 Następujące kroki są przeznaczone do wdrożenia systemu operacyjnego niestandardowej sekwencji zadań:  

-   [Sprawdź gotowość](../understand/task-sequence-steps.md#BKMK_CheckReadiness)  

-   [Połącz z folderem sieciowym](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder)  

-   [Pobierz zawartość pakietu](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent)  

-   [Instalowanie aplikacji](../understand/task-sequence-steps.md#BKMK_InstallApplication)  

-   [Zainstaluj pakiet](../understand/task-sequence-steps.md#BKMK_InstallPackage)  

-   [Instalacja aktualizacji oprogramowania](../understand/task-sequence-steps.md#BKMK_InstallSoftwareUpdates)  

-   [Uruchom ponownie komputer](../understand/task-sequence-steps.md#a-namebkmkrestartcomputera-restart-computer)  

-   [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine)  

-   [Uruchom skrypt programu PowerShell](../understand/task-sequence-steps.md#BKMK_RunPowerShellScript)  

-   [Ustaw zmienne dynamiczne](../understand/task-sequence-steps.md#BKMK_SetDynamicVariables)  

-   [Ustaw zmienną sekwencji zadań](../understand/task-sequence-steps.md#BKMK_SetTaskSequenceVariable)  

## <a name="next-steps"></a>Następne kroki
[Wdrożenie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#a-namebkmkdeploytsa-deploy-a-task-sequence)

