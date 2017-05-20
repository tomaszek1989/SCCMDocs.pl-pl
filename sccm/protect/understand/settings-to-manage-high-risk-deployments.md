---
title: "Zarządzanie wdrożeniami o wysokim ryzyku | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak skonfigurować ustawienia lokacji w System Center Configuration Manager do warn Administratorzy tworzenia wdrożenie o wysokim ryzyku."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 8d37b983-a964-402c-819d-2512ed2d463b
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bff083fe279cd6b36a58305a5f16051ea241151e
ms.openlocfilehash: 8b5564f39f07a67a3c9278379ed59ca415603d21
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="settings-to-manage-high-risk-deployments-for-system-center-configuration-manager"></a>Ustawienia zarządzania wdrożeniami o wysokim ryzyku dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Z System Center Configuration Manager można skonfigurować ustawienia lokacji, powiadomi Administratorzy tworzenia wdrożenia sekwencji zadań o wysokim ryzyku. Wdrożenie o wysokim ryzyku to:  

-   wdrożenie instalowane automatycznie,  

-   mogące potencjalnie dać niepożądane wyniki.  

 Na przykład sekwencji zadań, która ma cel **wymagane** która wdraża system operacyjny jest traktowane jako o wysokim ryzyku.  

 Aby zmniejszyć ryzyko niepożądanych wdrożenie o wysokim ryzyku, można skonfigurować limity rozmiaru w te ustawienia weryfikacji wdrażania:  

-   **Limity rozmiaru kolekcji**: Ukryj kolekcje zawierające większej liczby klientów niż limit podczas tworzenia wdrożenia.  

    -   **Domyślny rozmiar**: To ustawienie powoduje ukrycie kolekcje, domyślnie z większej liczby klientów niż limit podczas tworzenia wdrożenia. Można również widzieć te kolekcje, podczas tworzenia wdrożenia, ale są domyślnie ukryte. Wartość domyślna to 100. Wprowadź wartość 0, aby zignorować to ustawienie.  

    -   **Maksymalny rozmiar**: To ustawienie zawsze ukrywa kolekcje z większej liczby klientów niż limit podczas tworzenia wdrożenia. Wartością domyślną jest 0, co powoduje ignorowanie tego ustawienia. Wartość **Maksymalny rozmiar** musi być większa od wartości **Rozmiar domyślny** .  

     Na przykład ustawić **domyślny rozmiar** do 100 i **maksymalny rozmiar** do 1000. Po utworzeniu wdrożenia wysokiego ryzyka, **Wybieranie kolekcji** okna będą wyświetlane tylko kolekcje, które zawierają mniej niż 100 klientów. W przypadku usunięcia zaznaczenia **Ukryj kolekcje z elementem członkowskim liczba większa niż siteâ€™ konfiguracji minimalny rozmiar s** ustawienie, w oknie zostaną wyświetlone kolekcji, które zawierają mniej niż 1000 klientów.  

-   **Kolekcje z serwerami systemu lokacji**: Blokuj wdrożenia lub Wymagaj weryfikacji przed utworzeniem wdrożenia, gdy komputer z rolą systemu lokacji zawiera kolekcję docelową. Gdy wdrożenie jest zablokowane, należy wybrać inną kolekcję, która spełnia kryteria weryfikacji wdrożenia.  

> [!NOTE]  
>  Wdrożenia wysokiego ryzyka są zawsze ograniczone do kolekcji niestandardowych, kolekcji tworzonych przez Ciebie i wbudowanej kolekcji **Nieznane komputery** . Podczas tworzeniu wdrożenia wysokiego ryzyka nie można wybrać wbudowanej kolekcji, takiej jak **Wszystkie systemy**.  

### <a name="to-configure-deployment-verification-for-a-site"></a>Aby skonfigurować weryfikację wdrożenia dla lokacji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >**konfiguracja lokacji** > **witryny**, a następnie wybierz lokację główną do skonfigurowania.  

2.  Na **Home** karcie w **właściwości** grupy, wybierz **właściwości**, a następnie wybierz **weryfikację wdrożenia** kartę.  

3.  Po ustawieniu konfiguracji, którego chcesz użyć, wybierz **OK** Aby zapisać konfigurację.  

### <a name="see-also"></a>Zobacz także  
 [Konfigurowanie lokacji i hierarchii programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-sites-and-hierarchies.md)

