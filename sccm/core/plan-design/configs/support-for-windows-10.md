---
title: Obsługa systemu Windows 10
titleSuffix: Configuration Manager
description: Więcej informacji na temat wersji systemu Windows 10, które są obsługiwane jako klienci i dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 877732c4095438b19a863335a4a0026b7b088b24
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="support-for-windows-10-in-system-center-configuration-manager"></a>Obsługa systemu Windows 10 w programie System Center Configuration Manager  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Więcej informacji na temat wersji systemu Windows 10, które program Configuration Manager obsługuje, w tym:
 -  Windows 10 jako klient programu Configuration Manager
 -  Windows Assessment and Deployment Kit (ADK) dla systemu Windows 10

## <a name="windows-10-as-a-client"></a>Windows 10 jako klienta
Configuration Manager próbuje zapewniają obsługę jako klienta dla każdej nowej wersji systemu Windows 10 tak szybko, jak to możliwe po ich udostępnieniu. Ponieważ produkty oddzielnych harmonogramów rozwoju i wersji, pomocy technicznej programu Configuration Manager udostępnia zależy od daty każdej staje się dostępny.

Na przykład wersji programu Configuration Manager obniży macierzy po [obsługi dla tej wersji](/sccm/core/servers/manage/current-branch-versions-supported) kończy się. Podobnie Obsługa wersji systemu Windows 10, takich jak Enterprise 2015 LTSB lub 1511 porzucania macierzy, gdy są usuwane z pomocy technicznej. Aby uzyskać więcej informacji, zobacz [przestarzałe systemy operacyjne](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-client#deprecated-client-operating-systems).


-   Następujące dodatkowe informacje o [obsługiwane systemy operacyjne dla klientów i urządzeń](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).
-   Jeśli używasz długoterminowe obsługi gałęzi programu Configuration Manager, zobacz [obsługiwane konfiguracje dla gałęzi obsługi długoterminowe](/sccm/core/understand/supported-configurations-for-ltsb).

| Wersja systemu Windows 10 | Menedżer konfiguracji 1706 | Menedżer konfiguracji 1710 | Menedżer konfiguracji 1802 |
|---------------------|-----|-----|-----|
| Enterprise 2015 LTSB            <!--10/14/2025-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| Enterprise 2016 LTSB            <!--10/13/2026-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1607   <br />(*Zobacz wersje*)   <!--04/10/2018-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1703   <br />(*Zobacz wersje*)   <!--10/09/2018-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1709   <br />(*Zobacz wersje*)   <!--04/09/2019-->   | ![Wstecznie zgodne](media/blue_compat.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |

<!-- lifecycle reference: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet -->

**Wersje:** Enterprise, Pro, Education, Pro Education   

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane**  |
|![Zgodny z backwards](media/blue_compat.png)  = **zgodny Backwards** -istniejące funkcje zarządzania klienta powinny działać w nowej wersji systemu Windows 10. Na przykład spis sprzętu, zapasy oprogramowania i aktualizacji oprogramowania. Firma Microsoft będzie dokumentu znane problemy lub ostrzeżenia. <br><br>Takie podejście daje możliwość wdrażania i zarządzania nimi nowej wersji systemu Windows, od razu z obsługą zgodności aplikacji i bez konieczności nowej wersji aktualizacji programu Configuration Manager. |
|![Nieobsługiwane](media/Red_X.png) = **nie jest obsługiwane**|

 > [!NOTE]
 > Począwszy od wersji 1802 programu Configuration Manager obsługuje klienta na urządzeniach z systemem Windows 10 ARM64. Istniejące funkcje zarządzania klient powinien współpracować z tych nowych urządzeń. Na przykład sprzętu i spisu oprogramowania, aktualizacji oprogramowania i zarządzania aplikacjami. Wdrożenie systemu operacyjnego nie jest obecnie obsługiwane. <!-- 1353704 --> 



## <a name="windows-10-adk"></a>Windows 10 ADK
Podczas wdrażania systemów operacyjnych w programie Configuration Manager [zestawu Windows ADK jest zależności zewnętrzne](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) jest wymagana.

W poniższej tabeli wymieniono wersje systemu Windows ADK 10 korzystające z różnymi wersjami programu Configuration Manager.

| Wersja zestawu Windows 10 ADK  | Menedżer konfiguracji 1706 | Menedżer konfiguracji 1710 | Menedżer konfiguracji 1802   |
|--------------------|-----|-----|-----|
| 1607  | ![Nieobsługiwane](media/Red_X.png)   | ![Nieobsługiwane](media/Red_X.png) | ![Nieobsługiwane](media/Red_X.png) |
| 1703  | ![Obsługiwane](media/green_check.png) | ![Wstecznie zgodne](media/blue_compat.png) | ![Wstecznie zgodne](media/blue_compat.png) |
| 1709  | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |

|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = **obsługiwane** — zaleca systemu Windows za pomocą zestawu Windows ADK, zgodna z wersją systemu Windows są wdrażane. Na przykład użyć Windows ADK dla systemu Windows 10 w wersji 1703 podczas wdrażania systemu Windows 10 w wersji 1703. Aby uzyskać więcej informacji dotyczących obsługi składników zestawu Windows ADK, zobacz [platformy obsługiwane przez narzędzia DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) i [wymagania dotyczące narzędzia USMT](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1). |
|![Wstecznie zgodne](media/blue_compat.png)  = **zapewniającej** — ta kombinacja nie jest testowana, ale powinny działać. Firma Microsoft będzie dokumentu znane problemy lub ostrzeżenia. |
|![Nieobsługiwane](media/Red_X.png) = **nie jest obsługiwane**|

 > [!Note]
 > Program Configuration Manager obsługuje tylko x86 i amd64 składników zestawu Windows 10 adk. Go nie obsługuje obecnie składniki arm i arm64. 