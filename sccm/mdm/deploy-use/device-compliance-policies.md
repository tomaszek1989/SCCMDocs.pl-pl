---
title: "Zasady zgodności urządzeń | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zarządzanie zasadami zgodności w programie System Center Configuration Manager do zapewnienia zgodności z dostępem warunkowym urządzeń zasad."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
caps.latest.revision: 18
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcaa2a9b5474e06bf344dc4fd47dbb160ea36297
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="device-compliance-policies-in-system-center-configuration-manager"></a>Zasady zgodności urządzeń w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

**Zasady zgodności** w programie System Center Configuration Manager definiują reguły i zasady ustawień, które urządzenia muszą być zgodne, aby jest uznawany za zgodny przez dostępu warunkowego. Zasady zgodności mogą być również wykorzystane do monitorowania i rozwiązywania problemów ze zgodnością urządzeń niezależnie od dostępu warunkowego.  


> [!IMPORTANT]  
>  W tym artykule opisano zasady zgodności dla urządzeń zarządzanych przez Microsoft Intune.    Zasady zgodności dla komputerów zarządzanych przez program System Center Configuration Manager zostały opisane w artykule [Zarządzanie dostępem do usług O365 dla komputerów zarządzanych przez program System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

 Zasady te obejmują wymagania, takich jak:  

-   Kody PIN i hasła, aby uzyskać dostęp do urządzenia

-   Szyfrowanie danych przechowywanych na urządzeniu

-   Określanie, czy urządzenie ma złamane zabezpieczenia lub odblokowany dostęp  

-   Czy poczta e-mail na urządzeniu jest zarządzana przez zasady usługi Intune, czy urządzenie jest raportowana jako niezdrowy przez usługę zaświadczania kondycji urządzeń systemu Windows.
-   Aplikacje, których nie można zainstalować na urządzeniu.


 Zasady zgodności wdraża się dla kolekcji użytkowników. W przypadku wdrożenia zasad zgodności dla użytkownika sprawdzana jest zgodność wszystkich urządzeń użytkownika.  

 W poniższej tabeli przedstawiono typy urządzeń obsługiwanych przez zasady zgodności oraz sposób postępowania z niezgodnymi ustawieniami w przypadku, gdy zasady są używane w celu zapewnienia dostępu warunkowego.  

|Reguła|Windows 8.1 i nowsze|System Windows Phone 8.1 lub nowszy|System iOS 6.0 lub nowszy|Android 4.0 i nowsze Samsung KNOX Standard 4.0 i nowsze, Android do pracy|  
|----------|---------------------------|---------------------------------|-----------------------|---------------------------|-----------------------------------------|  
|**Konfiguracja kodu PIN lub hasła**|Skorygowane|Skorygowane|Skorygowane|Poddane kwarantannie|  
|**Szyfrowanie urządzenia**|Brak|Skorygowane|Skorygowane (przez ustawienie kodu PIN)|Poddane kwarantannie<br>(System android pracy zawsze szyfrowane)|  
|**Złamane zabezpieczenia lub urządzenia z możliwością dostępu**|Brak|Brak|Poddane kwarantannie (to nie jest ustawienie)|Poddane kwarantannie (to nie jest ustawienie)|  
|**Profil e-mail**|Brak|Brak|Poddane kwarantannie|Brak|  
|**Minimalna wersja systemu operacyjnego**|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|  
|**Maksymalna wersja systemu operacyjnego**|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|Poddane kwarantannie|  
|**Poświadczenie zdrowia urządzenia (1602 update)**|Ustawienie nie dotyczy systemu Windows 8.1<br /><br /> Systemy Windows 10 i Windows 10 Mobile są objęte kwarantanną.|Brak|Brak|Brak|  
|**Aplikacje, których nie można zainstalować**|Brak|Brak|Kwarantanna|Poddane kwarantannie|

 **Skorygowane** — zgodność jest wymuszana przez system operacyjny urządzenia (na przykład system wymusza na użytkowniku ustawienie kodu PIN).  Nigdy nie wystąpi niezgodność tego ustawienia.  

 **Poddane kwarantannie** — system operacyjny urządzenia nie wymusza zgodności (na przykład urządzenie z systemem Android nie wymusza na użytkowniku szyfrowania urządzenia).  W takim przypadku:  

-   Urządzenie zostanie zablokowane, jeśli użytkownik podlega zasadom dostępu warunkowego.  

-   Portal firmy lub portal sieci Web powiadomi użytkownika o wszelkich problemach ze zgodnością.  


### <a name="next-steps"></a>Następne kroki  
[Tworzenie i wdrażanie zasad zgodności urządzeń](create-compliance-policy.md)
### <a name="see-also"></a>Zobacz także  
 [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md)

