---
title: "Zasady zgodności urządzeń"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zarządzanie zasadami zgodności programu System Center Configuration Manager w celu zapewnienia zgodności z dostępu warunkowego urządzeń zasady."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
caps.latest.revision: "18"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: d9811d81987e8531ee48a07a6855b337fdccb73b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="device-compliance-policies-in-system-center-configuration-manager"></a>Zasady zgodności urządzeń w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

**Zasady zgodności** w programie System Center Configuration Manager definiują reguły i zasady ustawień, które urządzenie musi spełniać, aby zostać uznane za zgodne przez funkcję dostępu warunkowego. Zasady zgodności mogą być również wykorzystane do monitorowania i rozwiązywania problemów ze zgodnością urządzeń niezależnie od dostępu warunkowego.  


> [!IMPORTANT]  
>  W tym artykule opisano zasady zgodności dla urządzeń zarządzanych przez program Microsoft Intune.    Zasady zgodności dla komputerów zarządzanych przez program System Center Configuration Manager zostały opisane w artykule [Zarządzanie dostępem do usług O365 dla komputerów zarządzanych przez program System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

 Zasady te obejmują wymagania, takich jak:  

-   Numer PIN i hasła w celu uzyskania dostępu do urządzenia

-   Szyfrowanie danych przechowywanych na urządzeniu

-   Określanie, czy urządzenie ma złamane zabezpieczenia lub odblokowany dostęp  

-   Czy poczta e-mail na urządzeniu jest zarządzana przez zasady usługi Intune, czy urządzenie jest zgłaszane w złej kondycji przez usługę zaświadczania o kondycji urządzenia systemu Windows.
-   Aplikacje, których nie można zainstalować na urządzeniu.


 Zasady zgodności wdraża się dla kolekcji użytkowników. W przypadku wdrożenia zasad zgodności dla użytkownika sprawdzana jest zgodność wszystkich urządzeń użytkownika.  

 W poniższej tabeli przedstawiono typy urządzeń obsługiwanych przez zasady zgodności oraz sposób postępowania z niezgodnymi ustawieniami w przypadku, gdy zasady są używane w celu zapewnienia dostępu warunkowego.  

|Reguła|Windows 8.1 i nowsze|System Windows Phone 8.1 lub nowszy|System iOS 6.0 lub nowszy|Android 4.0 i nowsze Samsung KNOX Standard 4.0 lub nowszy, system Android for Work|  
|----------|---------------------------|---------------------------------|-----------------------|---------------------------|-----------------------------------------|  
|**Konfiguracja kodu PIN lub hasła**|Skorygowane|Skorygowane|Skorygowane|Poddane kwarantannie|  
|**Szyfrowanie urządzenia**|Brak|Skorygowane|Skorygowane (przez ustawienie kodu PIN)|Poddane kwarantannie<br>(System android for Work zawsze szyfrowane)|  
|**Ze zdjętymi zabezpieczeniami lub odblokowanym dostępem**|Brak|Brak|Poddane kwarantannie (to nie jest ustawienie)|Poddane kwarantannie (to nie jest ustawienie)|  
|**Profil e-mail**|Brak|Brak|Poddane kwarantannie|Brak|  
|**Minimalna wersja systemu operacyjnego**|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|  
|**Maksymalna wersja systemu operacyjnego**|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|  
|**Zaświadczanie o kondycji urządzenia (aktualizacja 1602)**|Ustawienie nie dotyczy systemu Windows 8.1<br /><br /> Systemy Windows 10 i Windows 10 Mobile są objęte kwarantanną.|Brak|Brak|Brak|  
|**Aplikacje, których nie można zainstalować**|Brak|Brak|Kwarantanna|Poddane kwarantannie|

 **Skorygowane** — zgodność jest wymuszana przez system operacyjny urządzenia (na przykład system wymusza na użytkowniku ustawienie kodu PIN).  Nigdy nie wystąpi niezgodność tego ustawienia.  

 **Poddane kwarantannie** — system operacyjny urządzenia nie wymusza zgodności (na przykład urządzenie z systemem Android nie wymusza na użytkowniku szyfrowania urządzenia).  W takim przypadku:  

-   Urządzenie zostanie zablokowane, jeśli użytkownik podlega zasadom dostępu warunkowego.  

-   Portal firmy lub portal sieci Web powiadomi użytkownika o wszelkich problemach ze zgodnością.  


### <a name="next-steps"></a>Następne kroki  
[Tworzenie i wdrażanie zasad zgodności urządzenia](create-compliance-policy.md)
### <a name="see-also"></a>Zobacz także  
 [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md)
