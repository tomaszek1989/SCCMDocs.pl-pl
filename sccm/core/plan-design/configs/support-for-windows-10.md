---
title: "Obsługa systemu Windows 10 | Dokumentacja firmy Microsoft"
description: "Informacje o wersji systemu Windows 10, które są obsługiwane jako klienci lub OSD z System Center Configuration Manager."
ms.custom: na
ms.date: 05/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 5
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ed5efcf7b305f8bee6e99e00c5285f6ae7033d82
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Obsługa systemu Windows 10 dla programu System Center Configuration Manager  

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Ten temat zawiera szczegóły wersji systemu Windows 10, korzystające z różnymi wersjami programu System Center Configuration Manager bieżącej gałęzi. Obejmuje to następujące działania:
 -  Windows 10 jako klient programu Configuration Manager.
 -  Windows 10 Windows Assessment and Deployment Kit (ADK).

## <a name="windows-10-as-a-client"></a>System Windows 10 jako klienta
Program Configuration Manager próbuje obsługi jako klienta dla każdej nowej wersji systemu Windows 10 jak najszybciej po wydań tej wersji systemu Windows. Ponieważ osobne harmonogramy opracowywania i wydawania produktów, pomocy technicznej, który zapewnia programu Configuration Manager zależy od daty wydania wersji i gałęzie każdego produktu.

Na przykład wersja programu Configuration Manager spowoduje porzucenie macierzy po [obsługi dla tej wersji](/sccm/core/servers/manage/current-branch-versions-supported) kończy się. Podobnie obsługę wersji systemu Windows 10, takich jak Enterprise 2015 LTSB lub 1607 (CBB) powoduje usunięcie z macierzy, usunięcie z listy obsługiwanych konfiguracji programu Configuration Manager. Zobacz [przestarzałe systemy operacyjne](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) uzyskać więcej informacji.

-   Następujące dodatkowe informacje [obsługiwanych systemów operacyjnych dla klientów i urządzeń](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Jeśli używasz długoterminowe obsługi gałęzi programu Configuration Manager, zobacz [Supported Configurations for gałęzi obsługi długoterminowe](/sccm/core/understand/supported-configurations-for-ltsb).

|Wersje systemu Windows 10                    |Menedżer konfiguracji 1606          |Menedżer konfiguracji 1610          |    Menedżer konfiguracji 1702 |
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1507 <br />(*Zobacz wersji*)            |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1511 (CB) (CBB)<br />(*Zobacz wersji*) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|Enterprise 2016 LTSB                   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1607 (CB)    <br />Rozliczenia aktualizacji<br />(*Zobacz wersji*)      |![Wstecz zgodne](media/blue_compat.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1607 (CBB)    <br />Rozliczenia aktualizacji<br />(*Zobacz wersji*)      |![Nieobsługiwane](media/Red_X.png)   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1703 (CB)    <br />Twórcy aktualizacji<br />(*Zobacz wersji*)      |![Nieobsługiwane](media/Red_X.png)   |![Nieobsługiwane](media/Red_X.png) |![Wstecz zgodne](media/blue_compat.png) |


**Wersje:** Enterprise, Pro, edukacja, edukacja Pro   

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane**  |
|![Nieobsługiwane](media/blue_compat.png)  = **zgodny z Backwards** -oznacza to, że istniejące funkcje zarządzania klienta (spisu sprzętu, spisu oprogramowania, aktualizacje oprogramowania itp.) powinny działać z nowej kompilacji systemu Windows 10 bieżącej gałęzi. Znane problemy lub ostrzeżenia zostanie udokumentowany. <br><br>Podejście to zapewnia kompilacje możliwość wdrażania i zarządzania nimi nowego systemu Windows 10 CB na jeden dzień z obsługą zgodności aplikacji bez konieczności nowej wersji aktualizacji programu Configuration Manager. |
|![Obsługiwane](media/Red_X.png) = **nie jest obsługiwane**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Podczas wdrażania systemów operacyjnych za pomocą programu Configuration Manager [Windows ADK to zewnętrzne zależności](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) jest wymagane.

Następująca tabela zawiera listę wersji zestawu Windows 10, korzystające z różnymi wersjami programu Configuration Manager.

|Wersji zestawu Windows 10 |Menedżer konfiguracji 1606 |Menedżer konfiguracji 1610  |Menedżer konfiguracji 1702 |
|--------------------|-----|-----|-----|
|1507  |![Nieobsługiwane](media/Red_X.png)         |![Nieobsługiwane](media/Red_X.png)  |![Nieobsługiwane](media/Red_X.png)|
|1511  |![Wstecz zgodne](media/blue_compat.png)|![Nieobsługiwane](media/Red_X.png)  |![Nieobsługiwane](media/Red_X.png)|
|1607  |![Obsługiwane](media/green_check.png)       |![Obsługiwane](media/green_check.png)|![Wstecz zgodne](media/blue_compat.png) |
|1703  |![Nieobsługiwane](media/Red_X.png)         |![Nieobsługiwane](media/Red_X.png)  |![Obsługiwane](media/green_check.png) |  

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane** — zaleca systemu Windows za pomocą zestawu Windows ADK zgodnej z wersją w przypadku wdrażania systemu Windows. Na przykład użyć Windows ADK dla systemu Windows 10 wersji 1703 podczas wdrażania systemu Windows 10 wersji 1703.  |
|![Wstecznie zgodna](media/blue_compat.png)  = **zapewniającej** -ta kombinacja nie został przetestowany, ale powinno ono działać. Znane problemy lub ostrzeżenia zostanie udokumentowany. |
|![Obsługiwane](media/Red_X.png) = **nie jest obsługiwane**|

