---
title: "Obsługa systemu Windows 10"
titleSuffix: Configuration Manager
description: "Informacje o wersji systemu Windows 10, które są obsługiwane jako klienci i dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager."
ms.custom: na
ms.date: 01/25/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 2dfe9b63e9e7c41a4f8457dc5622f386c7cceec2
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="support-for-windows-10-for-system-center-configuration-manager"></a>Obsługa systemu Windows 10 dla programu System Center Configuration Manager  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 Ten temat zawiera szczegóły dotyczące wersji systemu Windows 10, korzystających z różnymi wersjami programu System Center Configuration Manager Current Branch. Ta obsługa obejmuje:
 -  Windows 10 jako klient programu Configuration Manager
 -  Windows Assessment and Deployment Kit (ADK) dla systemu Windows 10

## <a name="windows-10-as-a-client"></a>Windows 10 jako klienta
Configuration Manager próbuje zapewniają obsługę jako klienta dla każdej nowej wersji systemu Windows 10 tak szybko, jak to możliwe po ich udostępnieniu. Ponieważ produkty oddzielnych harmonogramów rozwoju i wersji, pomocy technicznej programu Configuration Manager udostępnia zależy od daty każdej staje się dostępny.

Na przykład wersji programu Configuration Manager obniży macierzy po [obsługi dla tej wersji](/sccm/core/servers/manage/current-branch-versions-supported) kończy się. Podobnie Obsługa wersji systemu Windows 10, takich jak Enterprise 2015 LTSB lub 1511 porzucania macierzy, gdy są usuwane z pomocy technicznej. Aby uzyskać więcej informacji, zobacz [przestarzałe systemy operacyjne](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-client#deprecated-client-operating-systems).


-   Następujące dodatkowe informacje o [obsługiwane systemy operacyjne dla klientów i urządzeń](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Jeśli używasz długoterminowe obsługi gałęzi programu Configuration Manager, zobacz [obsługiwane konfiguracje dla gałęzi obsługi długoterminowe](/sccm/core/understand/supported-configurations-for-ltsb).

|Wersja systemu Windows 10                    |  Menedżer konfiguracji 1702          |    Menedżer konfiguracji 1706 |Menedżer konfiguracji 1710          |  
|---------------------|-----|-----|-----|
|Enterprise 2015 LTSB                   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
|Enterprise 2016 LTSB                   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
|1607   <br />(Znanej także jako aktualizacja rocznicy)<br />(*Zobacz wersje*)   |![Obsługiwane](media/green_check.png) |![Obsługiwane](media/green_check.png)            |![Obsługiwane](media/green_check.png) |
|1703   <br />(Znanej także jako aktualizacja twórców)<br />(*Zobacz wersje*)      |![Wstecznie zgodne](media/blue_compat.png) |![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
|1709   <br />(Znanej także jako aktualizacja twórców spadek)<br />(*Zobacz wersje*) |![Nieobsługiwane](media/Red_X.png)   |![Wstecznie zgodne](media/blue_compat.png) | ![Obsługiwane](media/green_check.png) |



**Wersje:** Enterprise, Pro, Education, Pro Education   

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane**  |
|![Nieobsługiwane](media/blue_compat.png)  = **zgodny Backwards** -istniejące funkcje zarządzania klienta (spisu sprzętu, spisu oprogramowania, aktualizacje oprogramowania itp.) powinny działać w nowej wersji systemu Windows 10. Firma Microsoft będzie dokumentu znane problemy lub ostrzeżenia. <br><br>Takie podejście daje możliwość wdrażania i zarządzania nimi nowych okien kompilacji na jeden dzień z obsługą zgodności aplikacji bez konieczności nowej wersji aktualizacji programu Configuration Manager. |
|![Obsługiwane](media/Red_X.png) = **nie jest obsługiwane**|


## <a name="windows-10-adk"></a>Windows 10 ADK
Podczas wdrażania systemów operacyjnych w programie Configuration Manager [zestawu Windows ADK jest zależności zewnętrzne](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) jest wymagana.

W poniższej tabeli wymieniono wersje systemu Windows ADK 10 korzystające z różnymi wersjami programu Configuration Manager.

|Wersja zestawu Windows 10 ADK  |Menedżer konfiguracji 1702   |Menedżer konfiguracji 1706 |Menedżer konfiguracji 1710 |
|--------------------|-----|-----|-----|
|1607  |![Wstecznie zgodne](media/blue_compat.png) |![Nieobsługiwane](media/Red_X.png)| ![Nieobsługiwane](media/Red_X.png) |
|1703  |![Obsługiwane](media/green_check.png)            |![Obsługiwane](media/green_check.png) | ![Wstecznie zgodne](media/blue_compat.png)|
|1709  |![Nieobsługiwane](media/Red_X.png)              |![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png)|

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane** — zaleca systemu Windows za pomocą zestawu Windows ADK, zgodna z wersją systemu Windows są wdrażane. Na przykład użyć Windows ADK dla systemu Windows 10 w wersji 1703 podczas wdrażania systemu Windows 10 w wersji 1703. Aby uzyskać więcej informacji dotyczących obsługi składników zestawu Windows ADK, zobacz [platformy obsługiwane przez narzędzia DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) i [wymagania dotyczące narzędzia USMT](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1). |
|![Wstecznie zgodne](media/blue_compat.png)  = **zapewniającej** — ta kombinacja nie jest testowana, ale powinny działać. Firma Microsoft będzie dokumentu znane problemy lub ostrzeżenia. |
|![Obsługiwane](media/Red_X.png) = **nie jest obsługiwane**|
