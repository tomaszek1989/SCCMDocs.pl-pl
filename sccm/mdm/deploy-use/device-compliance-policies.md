---
title: Zasady zgodności urządzeń
titleSuffix: Configuration Manager
description: Dowiedz się, jak zarządzanie zasadami zgodności programu System Center Configuration Manager w celu zapewnienia zgodności z dostępu warunkowego urządzeń zasady.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: ad8fa94d-45bb-4c94-8d86-31234c5cf21c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 776af7499c576f21d47dafec8a668f3c4051ad88
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
|**Aplikacje, których nie można zainstalować**|Brak|Brak|Poddane kwarantannie|Poddane kwarantannie|

 **Skorygowane** — zgodność jest wymuszana przez system operacyjny urządzenia (na przykład system wymusza na użytkowniku ustawienie kodu PIN).  Nigdy nie wystąpi niezgodność tego ustawienia.  

 **Poddane kwarantannie** — system operacyjny urządzenia nie wymusza zgodności (na przykład urządzenie z systemem Android nie wymusza na użytkowniku szyfrowania urządzenia).  W takim przypadku:  

-   Urządzenie zostanie zablokowane, jeśli użytkownik podlega zasadom dostępu warunkowego.  

-   Portal firmy lub portal sieci Web powiadomi użytkownika o wszelkich problemach ze zgodnością.  


### <a name="next-steps"></a>Następne kroki  
[Tworzenie i wdrażanie zasad zgodności urządzenia](create-compliance-policy.md)
### <a name="see-also"></a>Zobacz także  
 [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md)
