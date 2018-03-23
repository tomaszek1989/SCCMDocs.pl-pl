---
title: CMG — CZĘSTO ZADAWANE PYTANIA
description: Niniejszy artykuł służy odpowiedzi na często zadawane pytania dotyczące zarządzania bramy chmury
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.assetid: 4c1a128d-22fb-49f1-8e0b-36513a8dc117
ms.openlocfilehash: 8615b28735165650a0ec25e3d3114263835803d6
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="frequently-asked-questions-about-the-cloud-management-gateway"></a>Często zadawane pytania dotyczące zarządzania bramy chmury

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera odpowiedzi na często zadawane pytania dotyczące brama zarządzania chmury. Aby uzyskać więcej informacji, zobacz [plan brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).


## <a name="frequently-asked-questions"></a>Często zadawane pytania

### <a name="what-certificates-do-i-need"></a>Jakie certyfikaty potrzebne?

Aby uzyskać szczegółowe informacje, zobacz [certyfikatów dla bramy zarządzania chmury](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway).


### <a name="do-i-need-azure-expressroute"></a>Czy muszą Azure ExpressRoute?

[Usługa Azure ExpressRoute](/azure/expressroute/expressroute-introduction) umożliwia rozszerzenie sieci lokalnej w chmurze firmy Microsoft. ExpressRoute lub inne połączenia sieci wirtualnej nie są wymagane do zarządzania bramy chmury programu Configuration Manager. Projekt chmury brama zarządzania umożliwia klientom internetowego komunikują się za pośrednictwem usługi Azure z lokalnymi systemami lokacji bez konieczności wykonywania dodatkowych sieci konfiguracyjnych. Aby uzyskać więcej informacji, zobacz [planowanie brama zarządzania w chmurze](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)

Jeśli Twoja organizacja korzysta z usługi ExpressRoute, najlepszym rozwiązaniem bezpieczeństwa jest odizolowanie subskrypcji platformy Azure w przypadku bram chmur zarządzania. Taka konfiguracja powoduje, że Usługa bramy zarządzania chmury przypadkowo niepołączonym w ten sposób. Aby uzyskać więcej informacji, zobacz [bezpieczeństwo i prywatność brama zarządzania chmury](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway).


### <a name="do-i-need-to-maintain-the-azure-virtual-machines"></a>Należy do obsługi maszyn wirtualnych platformy Azure?

Nie obsługi jest wymagana. Projekt chmury brama zarządzania korzysta z platformy Azure jako usługa (PaaS). Korzystanie z subskrypcji, podane przez użytkownika, programu Configuration Manager tworzy niezbędne maszynach wirtualnych (VM), magazynu i sieci. Azure zabezpiecza i aktualizuje maszyny wirtualnej. Te maszyny wirtualne nie są częścią w lokalnym środowisku, tak jak w przypadku infrastruktura jako usługa (IaaS). Brama zarządzania chmury jest PaaS, rozszerzający środowiska programu Configuration Manager do chmury. 


### <a name="im-already-using-ibcm-if-i-add-cmg-how-do-clients-behave"></a>IBCM już jest używany. Czy mogę dodać CMG, zachowania klientów?

Jeśli została już wdrożona [zarządzania klientami internetowymi](/sccm/core/clients/manage/plan-internet-based-client-management) (IBCM), można także wdrożyć brama zarządzania chmury. Klienci otrzymują zasady dla obu usług. Jak są one przekazywane do Internetu, ich losowo wybierz i użyj jednej z tych usług internetowych.


## <a name="next-steps"></a>Następne kroki

- [Planowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
- [Konfigurowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
- [Certyfikaty bramy zarządzania w chmurze](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [Bezpieczeństwo i prywatność brama zarządzania w chmurze](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [Rozmiar bramy zarządzania w chmurze i skalowanie liczb](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)