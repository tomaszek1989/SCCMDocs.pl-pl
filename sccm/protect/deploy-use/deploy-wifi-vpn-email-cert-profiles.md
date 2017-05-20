---
title: "Wdrażanie sieci Wi-Fi, sieci VPN, profile certyfikatów oraz wiadomości e-mail | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie wdrażania sieci Wi-Fi, sieci VPN, poczty e-mail i profili certyfikatów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3753608d-b539-44dc-8e3f-b631319e7687
caps.latest.revision: 5
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c2e3aef41e9a890d136039f85777ab07284e5c27
ms.openlocfilehash: 70372d5df13034b48f3e43b766776442f1be5823
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="deploy-profiles-in-system-center-configuration-manager"></a>Wdrażanie profili w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Profile należy wdrożyć do jednej lub kilku kolekcjach przed ich użyciem.  

 Użyj **Wdrażanie profilu sieci Wi-Fi**, **Wdrażanie profilu sieci VPN**, **Wdrażanie profilu programu Exchange ActiveSync**, lub **Wdróż profil certyfikatu** okno dialogowe, aby skonfigurować wdrożenie tych profilów. W ramach konfiguracji należy zdefiniować kolekcję, do których profil jest można wdrożyć i określić, jak często profil jest sprawdzany pod kątem zgodności.  

> [!NOTE]  
>  Wdrożenie wielu profili dostępu do zasobów firmy dla tego samego użytkownika spowoduje następujące zachowanie:  
>   
>  -   Jeśli sprzeczne ustawienie zawiera wartość opcjonalną, nie zostanie ono wysyłane do urządzenia.  
> -   Jeśli sprzeczne ustawienie zawiera wartość obowiązkową, do urządzenia zostanie wysłana wartość domyślna. W przypadku braku wartości domyślnej przesyłanie profilu dostępu do zasobów całej firmy zakończy się niepowodzeniem. Na przykład jeśli są wdrażane dwa profile poczty e-mail dla tego samego użytkownika i wartości określone dla opcji **Host programu Exchange ActiveSync** lub **Adres e-mail** różnią się, dla obu profili poczty e-mail wystąpi błąd, ponieważ są to ustawienia obowiązkowe.  

> -   Przed wdrożeniem profili certyfikatów należy skonfigurować infrastrukturę i utworzyć profile certyfikatów. Więcej informacji znajduje się w następujących tematach:  
>   
>  -   [Konfigurowanie infrastruktury certyfikatów w programie System Center Configuration Manager](certificate-infrastructure.md)  
> -   [Tworzenie profili certyfikatów w programie System Center Configuration Manager](create-certificate-profiles.md)    

> [!IMPORTANT]  
>  Po usunięciu wdrożenia profilu sieci VPN nie jest usuwany z urządzeń klientów. Aby usunąć profil z urządzeń, należy zrobić to ręcznie.
>   

## <a name="deploying--profiles"></a>Wdrażanie profilów  


1.  W konsoli programu System Center Configuration Manager wybierz **zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, rozwiń węzeł **dostęp do zasobów firmy**, a następnie wybierz odpowiedni profil typu, takich jak **profilów sieci Wi-Fi**.  

3.  Na liście profilów wybierz profil, który chcesz wdrożyć, a następnie w **Home** w karcie **wdrożenia** , kliknij przycisk **Wdróż**.  

4.  W oknie dialogowym Wdróż profilu Podaj następujące informacje:  

    -   **Kolekcja** -kliknij **Przeglądaj** aby wybrać kolekcję, w której chcesz wdrożyć profil.  

    -   **Generowanie alertu** — Włącz tę opcję skonfigurować alert generowany, jeżeli zgodność profilu jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

    -   -   **Opóźnienie losowe (w godzinach)**: (Tylko w przypadku profili certyfikatów zawierających ustawienia prostego protokołu rejestrowania certyfikatów) Określa okno opóźnienia, aby uniknąć nadmiernego przetwarzania usługi rejestracji urządzeń sieciowych. Domyślna wartość to **64** godziny.  

    -   **Określ harmonogram oceny zgodności dla tego <type> profilu** — Określ harmonogram oceny wdrożonego profilu na komputerach klienckich. Harmonogram może być prosty lub niestandardowy.  

        > [!NOTE]  
        >  Klienci oceniają profile po zalogowaniu się użytkownika.  

5.  Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć wdrożenie.

### <a name="see-also"></a>Zobacz także  

[Monitorowanie sieci Wi-Fi, sieci VPN i profile poczty e-mail w programie System Center Configuration Manager](monitor-wifi-email-vpn-profiles.md)

[Monitorowanie profili certyfikatów w programie System Center Configuration Manager](monitor-certificate-profiles.md)

