---
title: "Włącz regułę ochrony urządzeń w zasadach zgodności | Dokumentacja firmy Microsoft"
description: "Włącz regułę ochrony przenośnych zagrożeń w zasadach zgodności urządzenia."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: faa92e150686e615164ce3f5435b77a65305aab3
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Włącz regułę ochrony zagrożeń urządzenia w zasadach zgodności

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Usługa Intune z ochrony przed zagrożeniami przenośnych Lookout daje możliwość wykrywać zagrożenia przenośnych i dokonać oceny ryzyka na urządzeniu. Można utworzyć regułę zasad zgodności w programie Configuration Manager do oceny ryzyka do ustalenia, czy urządzenie jest zgodne. Następnie można zasad dostępu warunkowego zezwala lub blokuje dostęp do programu Exchange, SharePoint i innych usług w oparciu o zgodności urządzenia.

Aby Lookout urządzenie wykrywanie zagrożeń wpływ zasad zgodności dla urządzenia:

* **Ochrony urządzenia przed zagrożeniami** należy włączyć regułę zasad zgodności.

* **Stan Lookout** strony **konsoli administratora usługi Intune** muszą wskazywać jako **Active**. Zobacz [włączyć usługę Lookout MTP połączenia w usłudze Intune](enable-lookout-connection-in-intune.md) tematu, aby uzyskać bardziej szczegółowe informacje i instrukcje dotyczące aktywowania Lookout integracji.


Przed utworzeniem reguły ochrony zagrożeń urządzenia w zasadach zgodności, zaleca się, że możesz [konfigurowania subskrypcji z ochrony Lookout urządzenia przed zagrożeniami](set-up-your-subscription-with-lookout.md), [Włącz w usłudze Intune połączenie Lookout](enable-lookout-connection-in-intune.md), i [skonfigurować aplikację Lookout for work aplikacji](configure-and-deploy-lookout-for-work-apps.md). Zasady zgodności, będą wymuszane tylko po zakończeniu instalacji.

Aby włączyć reguły ochrony zagrożeń urządzenia, można użyć istniejących zasad dotyczących zgodności lub Utwórz nową.

W ramach instalacji ochrony zagrożeń urządzenia Lookout w [konsoli Lookout](https://aad.lookout.com), utworzyć zasadę, która klasyfikuje różne zagrożenia w poziomach wysoki, średni i niski. Poziom zagrożenia zasadami zgodności usługi Intune umożliwia Ustaw poziom maksymalny dozwolony zagrożenia.

Na **reguły** strony Kreatora zasad zgodności, należy zdefiniować nową regułę z następującymi informacjami:
  * Warunek: Poziom ochrony maksymalną ryzyko zagrożeń urządzenia.
  * Wartość: Wartość może być jedną z następujących czynności:
    * **Brak (zabezpieczony)**: Jest to najbardziej bezpieczna. Oznacza to, że urządzenie nie może mieć żadnych zagrożeń. W przypadku znalezienia dowolny poziom zagrożenia urządzenia jest oceniana jako niezgodna.
    * **Niski**: Urządzenie jest uznane za zgodne, jeśli tylko występują niskiego poziomu zagrożenia. Urządzenie niczego wyższej umieszcza niezgodnych stan.
    * **Średnia liczba godzin**: Urządzenie jest traktowane jako zgodne, jeśli poziom małych i średnich zagrożeń znajdujące się w urządzeniu. Wykrycie wysoki poziom zagrożenia urządzenia jest określana jako niezgodne.
    * **Wysoka**: Jest to najmniej bezpieczna. Zasadniczo dzięki temu wszystkie poziomy zagrożeń i być może jest to przydatne tylko jeśli używasz tego rozwiązania tylko do celów raportowania.

Po utworzeniu zasad dostępu warunkowego dla usługi Office 365 i innych usług powyższej oceny zgodności jest brana pod uwagę i niezgodne urządzenia będą miały dostępu do zasobów firmy do czasu rozwiązania to zagrożenie.

Stan ochrony zagrożeń urządzenia jest wyświetlany na **zabezpieczeń** w węźle **monitorowanie** obszaru roboczego.
Podsumowanie stanu różnych poziomu wątku jest wyświetlany na wykresie visual. Możesz kliknąć poszczególne sekcje na wykresie, aby zobaczyć więcej informacji, takich jak, liczba urządzeń podlegających jako niezgodne przez platformy, a wszelkie błędy, które są zgłaszane.
Można również zobaczyć stan poszczególnych urządzeń w **zasoby i zgodność** obszaru roboczego, w obszarze **urządzeń**.  Możesz dodać **zgodności urządzeń za zagrożenie** i **poziom zagrożenia urządzenia** kolumn, aby wyświetlić stan.  Te kolumny nie są wyświetlane domyślnie.
