---
title: "Lokalnego zarządzania urządzeniami przenośnymi (MDM) | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zarządzania urządzeniami przenośnymi lokalnie, rozwiązanie do zarządzania urządzeniami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
caps.latest.revision: 8
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 7b96c4d4d87aa150eacc5d7d20710f5d2199e48a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="on-premises-mobile-device-management-mdm-in-system-center-configuration-manager"></a>Lokalnego zarządzania urządzeniami przenośnymi (MDM) programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager na\-lokalnych zarządzanie urządzeniami przenośnymi jest rozwiązanie do zarządzania urządzeniami, który zależy od możliwości zarządzania wbudowane systemy operacyjne (oparte na standardzie Open Mobile Alliance urządzenia zarządzania lub OMA-DM) podczas korzystania z infrastruktury programu Configuration Manager w przedsiębiorstwie do zarządzania i obsługa urządzeń. Na\-lokalnych zarządzanie urządzeniami przenośnymi wymaga Microsoft Intune ustanowienie możliwości zarządzania, ale jest wymagana tylko dla subskrypcji (i w czasie, aby pomóc powiadomić urządzeń, aby zaewidencjonować zmiany zasad), ale nie jest używana do zarządzania urządzeniami lub przechowywać dane o nich.  

 ![Na\-lokalnego koncepcyjny](media/On-premises-conceptual.png)  

 Na\-lokalnej zarządzanie urządzeniami przenośnymi różni się od firmy Microsoft Intune, który również jest zależna od wbudowanych możliwości OMA DM, ale wszystkie funkcje zarządzania są dostarczane za pośrednictwem usług w chmurze.  Na\-lokalnego zarządzania urządzeniami przenośnymi również różni się od rozwiązanie do zarządzania klienckich tradycyjnie oferowane przez program Configuration Manager, w tym opiera się na podobne infrastruktury przedsiębiorstwa, ale nie używać osobno zainstalowania oprogramowania klienta na komputerach i urządzeniach zarządza.  

 W poniższej tabeli przedstawiono zalety i wady w\-lokalnych zarządzanie urządzeniami przenośnymi w porównaniu do tradycyjnych zarządzania klienckich:  

|Zalety|Wady|  
|----------------|-------------------|  
|**Uproszczona infrastruktura** — wymaganych jest mniej ról systemu lokacji.<br /><br /> **Łatwiejszy w utrzymaniu** -funkcji zarządzania jest wbudowana w system operacyjny urządzenia, nowe wersje oprogramowania klienckiego nie są wymagane, gdy wprowadzono nowe funkcje zarządzania w systemie programu Configuration Manager.<br /><br /> **Rozwiązanie lokalne** — wszystkie funkcje zarządzania i dane są obsługiwane lokalnie.|**Mniej funkcji zarządzania klientami** — brak funkcji aranżacji, pomiaru użytkowania oprogramowania, integracji z rozwiązaniami innych firm, tworzenia sekwencji zadań i obsługi Centrum oprogramowania.<br /><br /> **Ograniczona obsługa urządzeń** — na\-lokalnego zarządzania urządzeniami przenośnymi obsługuje tylko urządzenia z systemem Windows 10 i Windows 10 Mobile.|  

 Poniższe tematy informacje służą do planowania, przygotowania i rejestrowanie urządzeń, na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Planowanie zarządzania urządzeniami przenośnymi lokalnego programu System Center Configuration Manager](../plan-design/plan-on-premises-mdm.md)  

     Dowiedz się więcej o tym, co należy wziąć pod uwagę podczas konfigurowania infrastruktury programu Configuration Manager i planowania do rejestracji urządzeń w na\-lokalnych zarządzanie urządzeniami przenośnymi.  

-   [Kroki przygotowania do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../get-started/preparation-steps-for-on-premises-mdm.md)  

     Więcej informacji na temat sposobu przygotowania systemu programu Configuration Manager do na\-lokalnego zarządzania urządzeniami przenośnymi, konfigurowanie subskrypcji usługi Microsoft Intune, konfigurowanie certyfikatów, instalowania ról systemu lokacji i konfigurowania rejestracji urządzeń.  

-   [Rejestrowanie urządzeń do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../deploy-use/enroll-devices-on-premises-mdm.md)  

     Informacje o przebiegu rejestracji, sposobie rejestrowania urządzeń przez użytkowników i sposobie zbiorczego rejestrowania urządzeń za pomocą pakietu rejestracyjnego.  

