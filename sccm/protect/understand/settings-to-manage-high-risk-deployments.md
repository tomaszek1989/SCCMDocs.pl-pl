---
title: "Zarządzanie wdrożeniami o wysokim ryzyku"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak skonfigurować ustawienia lokacji programu System Center Configuration Manager ostrzec administratorów o tworzeniu wdrożenia wysokiego ryzyka."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: "6"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 96855503183c1f9a3b51c5861ca661089f3c2994
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="settings-to-manage-high-risk-deployments-for-system-center-configuration-manager"></a>Ustawienia zarządzania wdrożeniami o wysokim ryzyku dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Z System Center Configuration Manager można skonfigurować ustawienia lokacji, które wyświetli ostrzeżenie administratorów o tworzeniu wdrożenia sekwencji zadań o wysokim ryzyku. Wdrożenie o wysokim ryzyku to:  

-   wdrożenie instalowane automatycznie,  

-   mogące potencjalnie dać niepożądane wyniki.  

 Na przykład sekwencji zadań, która ma cel **wymagane** która wdraża system operacyjny jest uznawany za o wysokim ryzyku.  

 Aby zmniejszyć ryzyko niepożądanych wdrożeń o wysokim ryzyku, można skonfigurować limity rozmiaru w te ustawienia weryfikacji wdrażania:  

-   **Limity rozmiaru kolekcji**: Ukryj kolekcje zawierające więcej klientów niż limit podczas tworzenia wdrożenia.  

    -   **Domyślny rozmiar**: To ustawienie powoduje ukrycie kolekcje, domyślnie zawierające więcej klientów niż limit podczas tworzenia wdrożenia. Nadal może wyświetlać takie kolekcje podczas tworzenia wdrożenia, ale są domyślnie ukryte. Wartość domyślna to 100. Wprowadź wartość 0, aby zignorować to ustawienie.  

    -   **Maksymalny rozmiar**: To ustawienie zawsze ukrywa kolekcje zawierające więcej klientów niż limit podczas tworzenia wdrożenia. Wartością domyślną jest 0, co powoduje ignorowanie tego ustawienia. Wartość **Maksymalny rozmiar** musi być większa od wartości **Rozmiar domyślny** .  

     Na przykład ustawić **domyślny rozmiar** do 100 i **maksymalny rozmiar** do 1000. Podczas tworzenia wdrożenia wysokiego ryzyka, **Wybieranie kolekcji** będą wyświetlane tylko kolekcje zawierające mniej niż 100 klientów. Jeśli wyczyścisz **Ukryj kolekcje z elementem członkowskim liczbą większą niż siteâ€™ s Minimalny rozmiar skonfigurowany** ustawienie, w oknie będą wyświetlane kolekcje zawierające mniej niż 1000 klientów.  

-   **Kolekcje z serwerami systemu lokacji**: Blokuje wdrożenie lub wymaga weryfikacji przed utworzeniem wdrożenia, jeśli kolekcja docelowa zawiera komputer z rolą systemu lokacji. Gdy wdrożenie jest zablokowane, należy wybrać inną kolekcję, która spełnia kryteria weryfikacji wdrożenia.  

> [!NOTE]  
>  Wdrożenia wysokiego ryzyka są zawsze ograniczone do kolekcji niestandardowych, kolekcji tworzonych przez Ciebie i wbudowanej kolekcji **Nieznane komputery** . Podczas tworzeniu wdrożenia wysokiego ryzyka nie można wybrać wbudowanej kolekcji, takiej jak **Wszystkie systemy**.  

### <a name="to-configure-deployment-verification-for-a-site"></a>Aby skonfigurować weryfikację wdrożenia dla lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji** >**konfiguracja lokacji** > **witryny**, a następnie wybierz lokację główną do skonfigurowania.  

2.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**, a następnie wybierz pozycję **weryfikację wdrożenia** kartę.  

3.  Po ustawieniu konfiguracji, którego chcesz użyć, wybierz **OK** Aby zapisać konfigurację.  

### <a name="see-also"></a>Zobacz także  
 [Konfigurowanie lokacji i hierarchii programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-sites-and-hierarchies.md)
