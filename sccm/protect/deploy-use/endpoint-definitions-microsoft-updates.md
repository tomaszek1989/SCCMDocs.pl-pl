---
title: "Definicje złośliwego oprogramowania Endpoint Protection z udziału sieciowego | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak włączyć pobieranie Endpoint Protection definicji złośliwego oprogramowania z usługi Microsoft Updates dla programu Configuration Manager."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ab7626ae-d4bf-4ca6-ab25-c61f96800a02
caps.latest.revision: 21
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 017bd5b899b364fc832c721d63cc7dbad0a11671
ms.openlocfilehash: 58c468fc3d4427cc1f2a8f197ab784a767151203
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="enable-endpoint-protection-malware-definitions-to-download-from-microsoft-updates-for-configuration-manager"></a>Włącz program Endpoint Protection definicji złośliwego oprogramowania do pobrania z usługi Microsoft Updates dla programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 W przypadku pobierania aktualizacji definicji przy użyciu usługi Microsoft Update klienci sprawdzają witrynę Microsoft Update w odstępach czasu zdefiniowanych w sekcji **Aktualizacje definicji** okna dialogowego zasad ochrony przed złośliwym kodem.

 Ta metoda może być przydatne, gdy klient nie ma łączności z lokacji programu Configuration Manager lub gdy użytkownicy mają mieć możliwość inicjowania aktualizacji definicji.

> [!IMPORTANT]
>  Klienci muszą mieć dostęp do usługi Microsoft Update w Internecie, aby można było użyć tej metody do pobierania aktualizacji definicji.

## <a name="using-the-microsoft-malware-protection-center-to-download-definitions"></a>Pobieranie definicji z Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem
 Klientów można skonfigurować do pobierania aktualizacji definicji z Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem. Ta opcja jest używana przez klientów programu Endpoint Protection, aby pobrać aktualizacje definicji, jeśli nie zostały jeszcze można pobrać aktualizacje z innego źródła. Metoda ta aktualizacja może być przydatne, jeśli występuje problem z infrastrukturą programu Configuration Manager, który uniemożliwia dostarczanie aktualizacji.

> [!IMPORTANT]
>  Klienci muszą mieć dostęp do usługi Microsoft Update w Internecie, aby można było użyć tej metody do pobierania aktualizacji definicji.


> [!div class="button"]
[Następny krok >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Ponownie >](endpoint-configure-alerts.md)

