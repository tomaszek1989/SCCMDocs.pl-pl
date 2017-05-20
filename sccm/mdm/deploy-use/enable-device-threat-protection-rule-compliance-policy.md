---
title: "Włącz regułę ochrony urządzenia w zasadach zgodności | Dokumentacja firmy Microsoft"
description: "Włącz regułę ochrony przenośnych zagrożenie w zasadach zgodności urządzeń."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99a5b715-f172-46e1-ac27-ad55bde66d0d
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: faa92e150686e615164ce3f5435b77a65305aab3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="enable-device-threat-protection-rule-in-the-compliance-policy"></a>Włącz zasadę ochrony zagrożenia urządzenia w zasadach zgodności

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Usługi Intune z przenośnych szczególną ochroną umożliwi to przywrócenie wykrywania zagrożeń przenośnych i ocenie ryzyka na urządzeniu. Można utworzyć regułę zasad zgodności w programie Configuration Manager do uwzględnienia w ocenie ryzyka, aby określić, czy urządzenie jest zgodne. Zasady dostępu warunkowego można następnie użyć do zezwalania lub blokowania dostępu do programu Exchange, SharePoint i innych usług, w oparciu o zgodności urządzenia.

Zapewnienie wykrywania zagrożeń urządzeń ewentualnym wywierania wpływu na zasady zgodności dla urządzenia:

* **Ochroną urządzenia** reguła musi zostać włączona w zasadach zgodności.

* **Stan ewentualnym** strony **konsoli administratora usługi Intune** wykazywać jako **Active**. Zobacz [włączyć MTP ewentualnym połączenia w usłudze Intune](enable-lookout-connection-in-intune.md) tematu bardziej szczegółowe informacje i instrukcje dotyczące aktywacji ewentualnym integracji.


Przed utworzeniem reguły ochrony zagrożenia urządzenia w zasadach compliancy, zaleca się możesz [konfigurowania subskrypcji z ochroną urządzenia ewentualnym](set-up-your-subscription-with-lookout.md), [Włącz połączenie ewentualnym w usłudze Intune](enable-lookout-connection-in-intune.md), i [skonfigurować szukać pracy aplikacji](configure-and-deploy-lookout-for-work-apps.md). Zasady zgodności wymuszane dopiero po zakończeniu pracy Instalatora.

Aby włączyć zasadę ochrony zagrożenia urządzenia, można użyć istniejących zasad zgodności lub Utwórz nową.

Jako część instalacji ochrony zagrożenia urządzenia szczególną w [konsoli ewentualnym](https://aad.lookout.com), utworzyć zasadę, która klasyfikuje różne zagrożenia na wysoki, średni i niski poziom. W zasadach zgodności Intune poziomu zagrożenia użyje ustawić poziom maksymalny dozwolony zagrożenia.

Na **reguły** strony Kreatora zasad zgodności, należy zdefiniować nową regułę z następującymi informacjami:
  * Warunek: Urządzenia zagrożenia ochrony ryzyka maksymalny poziom.
  * Wartość: Wartością może być jedną z następujących czynności:
    * **Brak (z zabezpieczeniami)**: Jest to najwyższy poziom bezpieczeństwa. Oznacza to, że urządzenie nie może mieć żadnych zagrożeń. Jeśli nie znaleziono żadnych poziomu zagrożenia, urządzenie jest obliczane jako niezgodny.
    * **Low**: Urządzenie jest szacowana jako zgodne, jeśli tylko niski poziom zagrożenia są obecne. Urządzenia niczego wyższe umieszcza w stanie niezgodny.
    * **Średnia**: Urządzenie jest obliczane jako zgodne, jeśli poziom niskiej lub średniej zagrożeń wykrytych w urządzeniu. W przypadku wysokiego poziomu zagrożenia urządzenie jest określana jako niezgodny.
    * **Wysoki**: Jest to najmniej bezpieczna. Zasadniczo dzięki temu wszystkie poziomy zagrożenia i być może jest to przydatne tylko jeśli używasz tego rozwiązania tylko na potrzeby raportowania.

W przypadku utworzenia zasad dostępu warunkowego dla usługi Office 365 i innych usług, powyższej oceny zgodności jest brana pod uwagę i niezgodne urządzenia będą miały dostępu do zasobów firmy, dopóki zagrożenie nie zostanie rozwiązany.

Stan urządzenia zagrożenia ochrony jest wyświetlany na **zabezpieczeń** w węźle **monitorowanie** obszaru roboczego.
Podsumowanie stanu z poziomu różnych wątku jest wyświetlany na wykresie visual. Można kliknąć poszczególne części wykresu, aby uzyskać więcej informacji, takich jak, liczba urządzeń raportowania jako niezgodny platformy i wszelkie zgłoszone błędy.
Możesz również sprawdzić stan poszczególnych urządzeń w **zasoby i zgodność** obszaru roboczego, w obszarze **urządzeń**.  Możesz dodać **zgodności urządzenia zagrożenia** i **poziomu zagrożenia urządzenia** kolumny, aby zobaczyć stan.  Te kolumny nie są domyślnie wyświetlane.

