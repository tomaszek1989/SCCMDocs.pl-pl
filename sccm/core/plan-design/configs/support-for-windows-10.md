---
title: "Obsługa systemu Windows 10 | Dokumentacja firmy Microsoft"
description: "Informacje o wersji systemu Windows 10, które są obsługiwane jako klienci i dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: "5"
author: brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 1d2e6e128531237ed76f94584aa42f76067db164
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Obsługa systemu Windows 10 dla programu System Center Configuration Manager  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 Ten temat zawiera szczegóły dotyczące wersji systemu Windows 10, korzystających z różnymi wersjami programu System Center Configuration Manager Current Branch. Obejmuje to następujące działania:
 -  Windows 10 jako klient programu Configuration Manager.
 -  Windows 10 Windows Assessment and Deployment Kit (ADK).

## <a name="windows-10-as-a-client"></a>Windows 10 jako klienta
Configuration Manager próbuje zapewniają obsługę jako klienta dla każdej nowej wersji systemu Windows 10 tak szybko, jak to możliwe po ich udostępnieniu. Ponieważ produkty oddzielnych harmonogramów rozwoju i wersji, pomocy technicznej programu Configuration Manager udostępnia zależy od daty każdej staje się dostępny.

Na przykład wersji programu Configuration Manager spowoduje porzucenie macierzy po [obsługi dla tej wersji](/sccm/core/servers/manage/current-branch-versions-supported) kończy się. Podobnie obsługę wersji systemu Windows 10 Enterprise 2015 LTSB lub 1511 porzuca macierzy, gdy są usuwane z pomocy technicznej. Zobacz [przestarzałe systemy operacyjne](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) Aby uzyskać więcej informacji.

-   Następujące dodatkowe informacje o [obsługiwane systemy operacyjne dla klientów i urządzeń](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Jeśli używasz długoterminowe obsługi gałęzi programu Configuration Manager, zobacz [obsługiwane konfiguracje dla gałęzi obsługi długoterminowe](/sccm/core/understand/supported-configurations-for-ltsb).

|Wersja systemu Windows 10                    |Menedżer konfiguracji 1610          |    Menedżer konfiguracji 1702          |    Menedżer konfiguracji 1706 |
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1511  <br />(*Zobacz wersje*)           |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|Enterprise 2016 LTSB                   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) |
|1607   <br />Aktualizacja rozliczenia<br />(*Zobacz wersje*)   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png)            |![Obsługiwane](media/green_check.png) |
|1703   <br />Twórcy aktualizacji<br />(*Zobacz wersje*)      |![Nieobsługiwane](media/Red_X.png)   |![Wstecznie zgodne](media/blue_compat.png) |![Obsługiwane](media/green_check.png) |


**Wersje:** Enterprise, Education Pro Pro, Education,   

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane**  |
|![Nieobsługiwane](media/blue_compat.png)  = **zgodny Backwards** -oznacza to, że istniejące funkcje zarządzania klienta (spisu sprzętu, spisu oprogramowania, aktualizacje oprogramowania itp.) powinny działać w nowej wersji systemu Windows 10. Znane problemy lub ostrzeżenia będą udokumentowane. <br><br>Takie podejście daje możliwość wdrażania i zarządzania nimi nowych okien kompilacji na jeden dzień z obsługą zgodności aplikacji bez konieczności nowej wersji aktualizacji programu Configuration Manager. |
|![Obsługiwane](media/Red_X.png) = **nie jest obsługiwane**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Podczas wdrażania systemów operacyjnych w programie Configuration Manager [zestawu Windows ADK jest zależności zewnętrzne](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) jest wymagana.

Następująca tabela zawiera listę wersji zestawu Windows 10 ADK korzystające z różnymi wersjami programu Configuration Manager.

|Wersja zestawu Windows 10 ADK  |Menedżer konfiguracji 1610 |Menedżer konfiguracji 1702   |Menedżer konfiguracji 1706 |
|--------------------|-----|-----|-----|
|1511  |![Nieobsługiwane](media/Red_X.png)             |![Nieobsługiwane](media/Red_X.png)              |![Nieobsługiwane](media/Red_X.png)|
|1607  |![Obsługiwane](media/green_check.png)           |![Wstecznie zgodne](media/blue_compat.png) |![Nieobsługiwane](media/Red_X.png)|
|1703  |![Nieobsługiwane](media/Red_X.png)             |![Obsługiwane](media/green_check.png)            |![Obsługiwane](media/green_check.png) |  

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane** — zaleca systemu Windows za pomocą zestawu Windows ADK, zgodna z wersją systemu Windows są wdrażane. Na przykład użyć Windows ADK dla systemu Windows 10 w wersji 1703 podczas wdrażania systemu Windows 10 w wersji 1703.  |
|![Wstecznie zgodne](media/blue_compat.png)  = **zapewniającej** — ta kombinacja nie jest testowana, ale powinny działać. Znane problemy lub ostrzeżenia będą udokumentowane. |
|![Obsługiwane](media/Red_X.png) = **nie jest obsługiwane**|
