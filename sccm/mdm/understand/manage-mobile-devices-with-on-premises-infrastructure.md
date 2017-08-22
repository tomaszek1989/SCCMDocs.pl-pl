---
title: "W ramach lokalnego zarządzania urządzeniami przenośnymi (MDM) | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zarządzania urządzeniami przenośnymi lokalnymi, rozwiązania do zarządzania urządzeniami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 497c05c7-fe9f-4b88-983b-1c5b3d59308e
caps.latest.revision: "8"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 7b96c4d4d87aa150eacc5d7d20710f5d2199e48a
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="on-premises-mobile-device-management-mdm-in-system-center-configuration-manager"></a>Lokalne zarządzanie urządzeniami przenośnymi (MDM) w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager na\-lokalnych zarządzanie urządzeniami przenośnymi jest rozwiązanie do zarządzania urządzeniami, które polega na wbudowanych funkcjach zarządzania systemów operacyjnych urządzeń (na podstawie standardu Open Mobile Alliance Device Management — OMA DM) podczas używania infrastrukturze programu Configuration Manager w celu zarządzania urządzeniami i ich obsługi. Na\-lokalnych zarządzanie urządzeniami przenośnymi wymaga programu Microsoft Intune do skonfigurowania funkcji zarządzania, ale jest to wymagane tylko dla subskrypcji (i w czasie, aby ułatwić powiadamiania urządzeń o konieczności zaewidencjonować zmiany zasad), ale nie jest on używany do zarządzania urządzeniami ani do przechowywania danych o nich.  

 ![Na\-lokalne koncepcyjne](media/On-premises-conceptual.png)  

 Na\-lokalne zarządzanie urządzeniami przenośnymi różni się od firmy Microsoft Intune, która również jest oparta na wbudowanych funkcjach standardu OMA DM, ale wszystkie funkcje zarządzania są dostarczane za pośrednictwem usługi w chmurze.  Na\-lokalne zarządzanie urządzeniami przenośnymi różni się również z rozwiązania do zarządzania opartego na kliencie tradycyjnie oferowane przez program Configuration Manager, w tym opiera się na podobnej infrastrukturze przedsiębiorstwa, ale nie używa oddzielnie zainstalowania oprogramowania klienta na komputerach i urządzeniach zarządza.  

 W poniższej tabeli wymieniono zalety i wady włączenia\-lokalnych zarządzanie urządzeniami przenośnymi w porównaniu do tradycyjnego zarządzania opartego na kliencie:  

|Zalety|Wady|  
|----------------|-------------------|  
|**Uproszczona infrastruktura** — wymaganych jest mniej ról systemu lokacji.<br /><br /> **Łatwiejsze w obsłudze** — ponieważ funkcje zarządzania są wbudowane w system operacyjny urządzenia, nowe wersje oprogramowania klienckiego nie są wymagane, gdy nowe funkcje zarządzania są wprowadzane do systemu programu Configuration Manager.<br /><br /> **Rozwiązanie lokalne** — wszystkie funkcje zarządzania i dane są obsługiwane lokalnie.|**Mniej funkcji zarządzania klientami** — brak funkcji aranżacji, pomiaru użytkowania oprogramowania, integracji z rozwiązaniami innych firm, tworzenia sekwencji zadań i obsługi Centrum oprogramowania.<br /><br /> **Ograniczona obsługa urządzeń** — aktualnie\-lokalne zarządzanie urządzeniami przenośnymi obsługuje tylko urządzenia z systemem Windows 10 i Windows 10 Mobile.|  

 Poniższe tematy zawierają informacje, można użyć do planowania, przygotowywania i rejestrowania urządzeń na potrzeby na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Planowanie lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../plan-design/plan-on-premises-mdm.md)  

     Dowiedz się więcej o tym, co należy wziąć pod uwagę podczas konfigurowania infrastruktury programu Configuration Manager i planowania rejestracji urządzeń w\-lokalnych zarządzanie urządzeniami przenośnymi.  

-   [Procedura przygotowująca do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../get-started/preparation-steps-for-on-premises-mdm.md)  

     Więcej informacji na temat sposobu przygotowania systemu programu Configuration Manager na\-lokalne zarządzanie urządzeniami przenośnymi, konfigurując subskrypcję Microsoft Intune, konfigurowanie certyfikatów, instalowania ról systemu lokacji, i konfigurując rejestrację urządzeń.  

-   [Rejestrowanie urządzeń do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../deploy-use/enroll-devices-on-premises-mdm.md)  

     Informacje o przebiegu rejestracji, sposobie rejestrowania urządzeń przez użytkowników i sposobie zbiorczego rejestrowania urządzeń za pomocą pakietu rejestracyjnego.  
