---
title: Obsługa systemu Windows 10
titleSuffix: Configuration Manager
description: Więcej informacji na temat wersji systemu Windows 10, które są obsługiwane jako klienci i dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager
ms.date: 04/30/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a1626a65-da22-49e0-9564-d2f752ea3f4b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 947392d4c11b419e0e373fbe83db42522d3c5f25
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="support-for-windows-10-in-system-center-configuration-manager"></a>Obsługa systemu Windows 10 w programie System Center Configuration Manager  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Więcej informacji na temat wersji systemu Windows 10, które program Configuration Manager obsługuje, w tym:
 -  [Windows 10 jako klient programu Configuration Manager](#windows-10-as-a-client)
 -  [Windows Assessment and Deployment Kit (ADK) dla systemu Windows 10](#windows-10-adk)



## <a name="windows-10-as-a-client"></a>Windows 10 jako klienta
Configuration Manager próbuje zapewniają obsługę jako klienta dla każdej nowej wersji systemu Windows 10 tak szybko, jak to możliwe po ich udostępnieniu. Ponieważ produkty oddzielnych harmonogramów rozwoju i wersji, pomocy technicznej programu Configuration Manager udostępnia zależy od daty każdej staje się dostępny.

Na przykład wersji programu Configuration Manager obniży macierzy po [obsługi dla tej wersji](/sccm/core/servers/manage/current-branch-versions-supported) kończy się. Podobnie Obsługa wersji systemu Windows 10, takich jak Enterprise 2015 LTSB lub 1511 porzucania macierzy, gdy są usuwane z pomocy technicznej. Aby uzyskać więcej informacji, zobacz [przestarzałe systemy operacyjne](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-client#deprecated-client-operating-systems).

-   Ta informacja uzupełnia [obsługiwane systemy operacyjne dla klientów i urządzeń](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices).  

-   Jeśli używasz długoterminowej gałęzi obsługi programu Configuration Manager, zobacz [obsługiwane konfiguracje dla długoterminowego gałęzi obsługi](/sccm/core/understand/supported-configurations-for-ltsb).  

<br/>
W poniższej tabeli wymieniono wersje systemu Windows 10, która służy jako klient z różnymi wersjami programu Configuration Manager.

| Wersja systemu Windows 10 | Menedżer konfiguracji 1706 | Menedżer konfiguracji 1710 | Menedżer konfiguracji 1802 |
|---------------------|-----|-----|-----|
| Enterprise 2015 LTSB            <!--10/14/2025-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| Enterprise 2016 LTSB            <!--10/13/2026-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1607   <br />(*Zobacz wersje*)   <!--04+6/10/2018-->   | ![Obsługiwane](media/green_check.png) <sup>1</sup> | ![Obsługiwane](media/green_check.png) <sup>1</sup> | ![Obsługiwane](media/green_check.png) <sup>1</sup> |
| 1703   <br />(*Zobacz wersje*)   <!--10+6/09/2018-->   | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1709   <br />(*Zobacz wersje*)   <!--04+6/09/2019-->   | ![Wstecznie zgodne](media/blue_compat.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1803   <br />(*Zobacz wersje*)   <!--11/12/2019-->   | ![Nieobsługiwane](media/Red_X.png) | ![Nieobsługiwane](media/Red_X.png) | ![Obsługiwane](media/green_check.png) |

<!-- lifecycle reference: https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet -->

**Wersje**: Enterprise, Pro, Education, Pro Education   

<sup>1</sup> uzyskać więcej informacji, zobacz [Windows cyklu życia faktów dotyczących](https://support.microsoft.com/help/13853/windows-lifecycle-fact-sheet) i sekcję "Rozszerzenie obsługi dla wersji Enterprise i Education".

| Klucz |
|--|
| ![Obsługiwane](media/green_check.png) = **obsługiwane**  |
| ![Zgodny z backwards](media/blue_compat.png)  = **Backwards zgodny** <br/> Istniejące funkcje zarządzania klienta powinny działać w nowej wersji systemu Windows 10. Na przykład spis sprzętu, zapasy oprogramowania i aktualizacji oprogramowania. Firma Microsoft będzie dokumentu znane problemy lub ostrzeżenia. <br><br>Takie podejście daje możliwość wdrażania i zarządzania nimi nowej wersji systemu Windows, od razu z obsługą zgodności aplikacji i bez konieczności nowej wersji aktualizacji programu Configuration Manager. |
| ![Nieobsługiwane](media/Red_X.png) = **nie jest obsługiwane** |

 > [!NOTE]  
 > Począwszy od wersji 1802 programu Configuration Manager obsługuje klienta na urządzeniach z systemem Windows 10 ARM64. Istniejące funkcje zarządzania klient powinien współpracować z tych nowych urządzeń. Na przykład sprzętu i spisu oprogramowania, aktualizacji oprogramowania i zarządzania aplikacjami. Wdrażanie systemu operacyjnego nie jest obecnie obsługiwane. <!-- 1353704 --> 



## <a name="windows-10-adk"></a>Windows 10 ADK
Podczas wdrażania systemów operacyjnych w programie Configuration Manager [zestawu Windows ADK jest zależności zewnętrzne](/sccm/osd/plan-design/infrastructure-requirements-for-operating-system-deployment) jest wymagana.

W poniższej tabeli wymieniono wersje systemu Windows ADK 10 korzystające z różnymi wersjami programu Configuration Manager.

| Wersja zestawu Windows 10 ADK  | Menedżer konfiguracji 1706 | Menedżer konfiguracji 1710 | Menedżer konfiguracji 1802   |
|--------------------|-----|-----|-----|
| 1703  | ![Obsługiwane](media/green_check.png) | ![Wstecznie zgodne](media/blue_compat.png) | ![Wstecznie zgodne](media/blue_compat.png) |
| 1709  | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) | ![Obsługiwane](media/green_check.png) |
| 1803  | ![Nieobsługiwane](media/Red_X.png)   | ![Nieobsługiwane](media/Red_X.png) | ![Obsługiwane](media/green_check.png) |

|Klucz|
|--|
| ![Obsługiwane](media/green_check.png) = **obsługiwane** <br/> System Windows zaleca za pomocą zestawu Windows ADK, która jest zgodna z wersją systemu Windows jest wdrażany. Na przykład użyć Windows ADK dla systemu Windows 10 w wersji 1703 podczas wdrażania systemu Windows 10 w wersji 1703. Aby uzyskać więcej informacji dotyczących obsługi składników zestawu Windows ADK, zobacz [platformy obsługiwane przez narzędzia DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-supported-platforms) i [wymagania dotyczące narzędzia USMT](https://docs.microsoft.com/windows/deployment/usmt/usmt-requirements#bkmk-1). |
| ![Wstecznie zgodne](media/blue_compat.png)  = **zgodne z poprzednimi wersjami** <br/> Ta kombinacja nie jest przetestowane, ale powinny działać. Firma Microsoft będzie dokumentu znane problemy lub ostrzeżenia. |
| ![Nieobsługiwane](media/Red_X.png) = **nie jest obsługiwane** |

 > [!Note]  
 > Program Configuration Manager obsługuje tylko x86 i amd64 składników zestawu Windows 10 adk. Aktualnie nie obsługuje składniki ARM i ARM64. 