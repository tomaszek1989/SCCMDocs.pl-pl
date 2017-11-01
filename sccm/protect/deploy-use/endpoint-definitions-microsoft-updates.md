---
title: "Definicje złośliwego oprogramowania ochrony punktu końcowego z udziału sieciowego"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak włączyć pobieranie definicji programu Endpoint Protection złośliwego oprogramowania z usługi Microsoft Updates programu Configuration Manager."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: ab7626ae-d4bf-4ca6-ab25-c61f96800a02
caps.latest.revision: "21"
author: NathBarn
ms.author: nathbarn
manager: angrobe
ms.openlocfilehash: af84a6da08407955f7e086038151c645956844e5
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="enable-endpoint-protection-malware-definitions-to-download-from-microsoft-updates-for-configuration-manager"></a>Włącz program Endpoint Protection definicje złośliwego oprogramowania można pobrać z usługi Microsoft Updates programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 W przypadku pobierania aktualizacji definicji przy użyciu usługi Microsoft Update klienci sprawdzają witrynę Microsoft Update w odstępach czasu zdefiniowanych w sekcji **Aktualizacje definicji** okna dialogowego zasad ochrony przed złośliwym kodem.

 Ta metoda może być przydatne, gdy klient nie ma łączności z lokacją programu Configuration Manager lub gdy użytkownicy mają mieć możliwość inicjowania aktualizacji definicji.

> [!IMPORTANT]
>  Klienci muszą mieć dostęp do usługi Microsoft Update w Internecie, aby można było użyć tej metody do pobierania aktualizacji definicji.

## <a name="using-the-microsoft-malware-protection-center-to-download-definitions"></a>Pobieranie definicji z Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem
 Klientów można skonfigurować do pobierania aktualizacji definicji z Centrum firmy Microsoft ds. ochrony przed złośliwym oprogramowaniem. Ta opcja jest używana przez klientów programu Endpoint Protection, aby pobierać aktualizacje definicji, jeśli nie zostały jeszcze może pobierać aktualizacje z innego źródła. Ta metoda aktualizacji może być przydatne, jeśli występuje problem z infrastruktury programu Configuration Manager, który uniemożliwia udostępnianie aktualizacji.

> [!IMPORTANT]
>  Klienci muszą mieć dostęp do usługi Microsoft Update w Internecie, aby można było użyć tej metody do pobierania aktualizacji definicji.


> [!div class="button"]
[Następny krok >](endpoint-antimalware-policies.md)

> [!div class="button"]
[Ponownie >](endpoint-configure-alerts.md)
