---

title: Skonfigurowanie programu Endpoint Protection | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak wybrać i skonfigurować metody z programem Endpoint Protection w programie System Center Configuration Manager do Aktualizuj definicje złośliwego oprogramowania na komputerach klienckich."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 537dd2a7-4e44-4877-b8dd-5e1499407f8d
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: b5da7900a4f8e2f330c4dcb2cac00b45099bd909
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017



---

#  <a name="configure-definition-updates-for-endpoint-protection"></a>Konfigurowanie aktualizacji definicji programu Endpoint Protection  

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Z programem Endpoint Protection w programie System Center Configuration Manager umożliwia dowolny z dostępnych kilka metod Aktualizuj definicje złośliwego oprogramowania na komputerach klienckich w hierarchii. Informacje przedstawione w tym temacie ułatwiają wybieranie i konfigurowanie tych metod.

 W celu zaktualizowania definicji oprogramowania chroniącego przed złośliwym kodem można użyć jednej lub kilku spośród następujących metod:

-   [Aktualizacje dystrybuowane z programu Configuration Manager](endpoint-definitions-configmgr.md) — ta metoda korzysta z aktualizacji oprogramowania programu Configuration Manager do dostarczenia aktualizacji aparatu i definicji na komputerach w hierarchii.

-   [Aktualizacje dystrybuowane z systemem Windows Server Update Services (WSUS)](endpoint-definitions-wsus.md) -metoda ta wykorzystuje infrastrukturę programu WSUS do dostarczenia aktualizacji aparatu i definicji na komputerach.

-   [Aktualizacje dystrybuowane z witryny Microsoft Update](endpoint-definitions-microsoft-updates.md) — ta metoda umożliwia komputerom połączyć się bezpośrednio z witryny Microsoft Update w celu pobrania aktualizacji aparatu i definicji. Ta metoda może być przydatna w przypadku komputerów, które nie są często podłączane do sieci firmowej.

-   [Aktualizacje dystrybuowane z Microsoft Malware Protection Center](endpoint-definitions-protection-center.md) — ta metoda ma pobrać aktualizacje definicji z Microsoft Malware Protection Center.

-   [Aktualizacje z udziałów plików UNC](endpoint-definitions-network.md) — przy użyciu tej metody można zapisać najnowszych aktualizacji aparatu i definicji do udziału w sieci. Następnie klienci mogą uzyskiwać dostęp do sieci w celu zainstalowania aktualizacji.

 Można skonfigurować wiele źródeł aktualizacji definicji i kontrolować kolejność, w jakiej są one oceniane i stosowane. Te czynności są wykonywane w oknie dialogowym **Konfigurowanie źródeł aktualizacji definicji** podczas tworzenia zasad ochrony przed złośliwym kodem.

> [!IMPORTANT]
>  Komputery z systemem Windows 10 należy skonfigurować Endpoint Protection aktualizacji definicji złośliwego oprogramowania dla usługi Windows Defender.

## <a name="how-to-configure-definition-update-sources"></a>Jak skonfigurować źródła aktualizacji definicji
 Poniższa procedura służy do konfigurowania źródeł aktualizacji definicji dla każdej zasady ochrony przed złośliwym kodem.

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Endpoint Protection**i kliknij pozycję **Zasady ochrony przed złośliwym kodem**.

3.  Otwórz stronę właściwości **domyślnych zasad ochrony przed złośliwym kodem** lub utwórz nowe zasady ochrony przed złośliwym kodem. Aby uzyskać więcej informacji na temat tworzenia zasad ochrony przed złośliwym oprogramowaniem, zobacz [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](endpoint-antimalware-policies.md).

4.  W sekcji **Aktualizacja definicji** okna dialogowego właściwości ochrony przed złośliwym kodem kliknij pozycję **Ustaw źródło**.

5.  W oknie dialogowym **Konfigurowanie źródeł aktualizacji definicji** wybierz źródła do użycia do aktualizacji definicji. Można kliknąć pozycję **W górę** lub **W dół** , aby zmodyfikować kolejność stosowania tych źródeł.

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Konfigurowanie źródeł aktualizacji definicji** .

## <a name="configure-endpoint-protection-definitions"></a>Konfigurowanie definicji programu Endpoint Protection

-   [Aktualizacje dystrybuowane z programu Configuration Manager](endpoint-definitions-configmgr.md) — ta metoda korzysta z aktualizacji oprogramowania programu Configuration Manager do dostarczenia aktualizacji aparatu i definicji na komputerach w hierarchii.

-   [Aktualizacje dystrybuowane z systemem Windows Server Update Services (WSUS)](endpoint-definitions-wsus.md) -metoda ta wykorzystuje infrastrukturę programu WSUS do dostarczenia aktualizacji aparatu i definicji na komputerach.

-   [Aktualizacje dystrybuowane z witryny Microsoft Update](endpoint-definitions-microsoft-updates.md) — ta metoda umożliwia komputerom połączyć się bezpośrednio z witryny Microsoft Update w celu pobrania aktualizacji aparatu i definicji. Ta metoda może być przydatna w przypadku komputerów, które nie są często podłączane do sieci firmowej.

-   Aktualizacje dystrybuowane z Microsoft Malware Protection Center — ta metoda pobierze aktualizacje definicji z Microsoft Malware Protection Center.

-   [Aktualizacje z udziałów plików UNC](endpoint-definitions-network.md) — przy użyciu tej metody można zapisać najnowszych aktualizacji aparatu i definicji do udziału w sieci. Następnie klienci mogą uzyskiwać dostęp do sieci w celu zainstalowania aktualizacji.

