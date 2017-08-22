---
title: "Tworzenie sekwencji zadań wdrożeń systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Tworzenie sekwencji zadań, które nie są powiązane z wdrażaniem systemów operacyjnych, takich jak dystrybucji oprogramowania, aktualizowania sterowników, edytowania stanu użytkowników itp."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92aaec8a-8751-442a-b64b-62ab05b5bf50
caps.latest.revision: "6"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: b4b04907f2cd48d81e864e46ca47c14a0b98a9f7
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-a-task-sequence-for-non-operating-system-deployments-with-system-center-configuration-manager"></a>Tworzenie sekwencji zadań dla wdrożeń systemu operacyjnego z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Sekwencje zadań w programie System Center Configuration Manager służą do automatyzacji wykonywania rozmaitych zadań w danym środowisku. Te zadania zostały utworzone i przetestowane głównie pod kątem wdrażania systemów operacyjnych.  Configuration Manager ma wiele innych funkcji, które powinny stanowić podstawową technologię używaną w scenariuszach, takich jak [instalacji aplikacji](../../apps/understand/introduction-to-application-management.md), [instalacja aktualizacji oprogramowania](../../sum/understand/software-updates-introduction.md), [konfiguracji](../../compliance/understand/ensure-device-compliance.md), i automatyzacja niestandardowa. Istnieją inne technologie automatyzacji programu Microsoft System Center, takie jak [Orchestrator](https://technet.microsoft.com/library/hh237242.aspx) i [Automatyzacja zarządzania usługami](https://technet.microsoft.com/library/dn469260.aspx) , które również należy rozważyć.  

Power sekwencji zadań znajduje się w ich elastyczność i jak ich używać do konfigurowania ustawień klienta, dystrybuowania oprogramowania, aktualizowania sterowników, edytowania stanu użytkowników i wykonywanie innych zadań niezależnie od wdrażania systemu operacyjnego. Można utworzyć niestandardową sekwencję zadań i dodać do niej dowolną liczbę zadań. Używanie niestandardowych sekwencji zadań wdrożenia systemu operacyjnego jest obsługiwane w programie Configuration Manager. Jednak jeśli wyniki sekwencji zadań w niechciane lub niespójne wyniki, obejrzyj sposobów, aby uprościć operacji. Można to zrobić za pomocą kroków prostszy, dzielenia akcje między wieloma sekwencje zadań, czy przez przełączenie etapowe podejścia do tworzenia i testowania sekwencji zadań.

 Następujące kroki są przeznaczone do wdrożenia systemu operacyjnego niestandardową sekwencję zadań:  

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
