---
title: Skonfigurowanie programu Endpoint Protection
titleSuffix: Configuration Manager
description: "Dowiedz się, jak wybrać i skonfigurować metody przy użyciu programu Endpoint Protection w System Center Configuration Manager do aktualne definicje złośliwego oprogramowania na komputerach klienckich."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 537dd2a7-4e44-4877-b8dd-5e1499407f8d
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: b0b178fad73b6490c4bfeb8ec4aaa7348e7cb2a2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
#  <a name="configure-definition-updates-for-endpoint-protection"></a>Konfigurowanie aktualizacji definicji programu Endpoint Protection  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Z programu Endpoint Protection w programie System Center Configuration Manager umożliwia dowolnej spośród kilku dostępnych metod aktualne definicje złośliwego oprogramowania na komputerach klienckich w hierarchii. Informacje przedstawione w tym temacie ułatwiają wybieranie i konfigurowanie tych metod.

 W celu zaktualizowania definicji oprogramowania chroniącego przed złośliwym kodem można użyć jednej lub kilku spośród następujących metod:

-   [Aktualizacje dystrybuowane z programu Configuration Manager](endpoint-definitions-configmgr.md) — ta metoda używa aktualizacji oprogramowania programu Configuration Manager do dostarczenia aktualizacji aparatu i definicji na komputerach w hierarchii.

-   [Aktualizacje dystrybuowane z systemem Windows Server Update Services (WSUS)](endpoint-definitions-wsus.md) — ta metoda używa infrastruktury programu WSUS do dostarczenia aktualizacji aparatu i definicji na komputerach.

-   [Aktualizacje dystrybuowane za pomocą usługi Microsoft Update](endpoint-definitions-microsoft-updates.md) — ta metoda umożliwia nawiązywanie połączeń bezpośrednio z witryną Microsoft Update w celu pobrania aktualizacji definicji i aparatu. Ta metoda może być przydatna w przypadku komputerów, które nie są często podłączane do sieci firmowej.

-   [Aktualizacje dystrybuowane za pomocą Microsoft Malware Protection Center](endpoint-definitions-protection-center.md) — ta metoda będą pobierać aktualizacje definicji z Microsoft Malware Protection Center.

-   [Aktualizacje z udziałów plików UNC](endpoint-definitions-network.md) — przy użyciu tej metody można zapisać najnowsze aktualizacje definicji i aparatu do udziału w sieci. Następnie klienci mogą uzyskiwać dostęp do sieci w celu zainstalowania aktualizacji.

 Można skonfigurować wiele źródeł aktualizacji definicji i kontrolować kolejność, w jakiej są one oceniane i stosowane. Te czynności są wykonywane w oknie dialogowym **Konfigurowanie źródeł aktualizacji definicji** podczas tworzenia zasad ochrony przed złośliwym kodem.

> [!IMPORTANT]
>  Dla komputerów z systemem Windows 10 należy skonfigurować program Endpoint Protection do aktualizacji definicji złośliwego oprogramowania dla usługi Windows Defender.

## <a name="how-to-configure-definition-update-sources"></a>Jak skonfigurować źródła aktualizacji definicji
 Poniższa procedura służy do konfigurowania źródeł aktualizacji definicji dla każdej zasady ochrony przed złośliwym kodem.

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Endpoint Protection**i kliknij pozycję **Zasady ochrony przed złośliwym kodem**.

3.  Otwórz stronę właściwości **domyślnych zasad ochrony przed złośliwym kodem** lub utwórz nowe zasady ochrony przed złośliwym kodem. Aby uzyskać więcej informacji dotyczących sposobu tworzenia zasad ochrony przed złośliwym kodem, zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

4.  W sekcji **Aktualizacja definicji** okna dialogowego właściwości ochrony przed złośliwym kodem kliknij pozycję **Ustaw źródło**.

5.  W oknie dialogowym **Konfigurowanie źródeł aktualizacji definicji** wybierz źródła do użycia do aktualizacji definicji. Można kliknąć pozycję **W górę** lub **W dół** , aby zmodyfikować kolejność stosowania tych źródeł.

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Konfigurowanie źródeł aktualizacji definicji** .

## <a name="configure-endpoint-protection-definitions"></a>Konfigurowanie definicji programu Endpoint Protection

-   [Aktualizacje dystrybuowane z programu Configuration Manager](endpoint-definitions-configmgr.md) — ta metoda używa aktualizacji oprogramowania programu Configuration Manager do dostarczenia aktualizacji aparatu i definicji na komputerach w hierarchii.

-   [Aktualizacje dystrybuowane z systemem Windows Server Update Services (WSUS)](endpoint-definitions-wsus.md) — ta metoda używa infrastruktury programu WSUS do dostarczenia aktualizacji aparatu i definicji na komputerach.

-   [Aktualizacje dystrybuowane za pomocą usługi Microsoft Update](endpoint-definitions-microsoft-updates.md) — ta metoda umożliwia nawiązywanie połączeń bezpośrednio z witryną Microsoft Update w celu pobrania aktualizacji definicji i aparatu. Ta metoda może być przydatna w przypadku komputerów, które nie są często podłączane do sieci firmowej.

-   Aktualizacje dystrybuowane za pomocą Microsoft Malware Protection Center — ta metoda będą pobierać aktualizacje definicji z Microsoft Malware Protection Center.

-   [Aktualizacje z udziałów plików UNC](endpoint-definitions-network.md) — przy użyciu tej metody można zapisać najnowsze aktualizacje definicji i aparatu do udziału w sieci. Następnie klienci mogą uzyskiwać dostęp do sieci w celu zainstalowania aktualizacji.
