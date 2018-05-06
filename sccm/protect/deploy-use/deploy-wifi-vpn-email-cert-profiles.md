---
title: Wdrażanie sieci Wi-Fi, VPN, poczty e-mail i profilów certyfikatów
titleSuffix: Configuration Manager
description: Dowiedz się, jak wdrożyć sieci Wi-Fi, VPN, poczty e-mail i profilów certyfikatów w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: 3753608d-b539-44dc-8e3f-b631319e7687
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: faf8d48614bc3e27381d57d86fc24da9356aa3f0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="deploy-profiles-in-system-center-configuration-manager"></a>Wdrażanie profilów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Profile należy wdrożyć w jednej lub kilku kolekcjach przed ich użyciem.  

 Użyj **Wdrażanie profilu sieci Wi-Fi**, **Wdróż profil VPN**, **Wdrażanie profilu programu Exchange ActiveSync**, lub **Wdróż profil certyfikatu** okno dialogowe umożliwia skonfigurowanie wdrażania profili. W ramach konfiguracji należy zdefiniować kolekcję, do której profil ma można wdrożyć i określ, jak często profil jest oceniane pod kątem zgodności.  

> [!NOTE]  
>  Wdrożenie wielu profili dostępu do zasobów firmy dla tego samego użytkownika spowoduje następujące zachowanie:  
>   
>  -   Jeśli sprzeczne ustawienie zawiera wartość opcjonalną, nie zostanie ono wysyłane do urządzenia.  
> -   Jeśli sprzeczne ustawienie zawiera wartość obowiązkową, do urządzenia zostanie wysłana wartość domyślna. W przypadku braku wartości domyślnej przesyłanie profilu dostępu do zasobów całej firmy zakończy się niepowodzeniem. Na przykład jeśli są wdrażane dwa profile poczty e-mail dla tego samego użytkownika i wartości określone dla opcji **Host programu Exchange ActiveSync** lub **Adres e-mail** różnią się, dla obu profili poczty e-mail wystąpi błąd, ponieważ są to ustawienia obowiązkowe.  

> -   Przed wdrożeniem profili certyfikatów należy skonfigurować infrastrukturę i utworzyć profile certyfikatów. Więcej informacji znajduje się w następujących tematach:  
>   
>  -   [Konfigurowanie infrastruktury certyfikatów w programie System Center Configuration Manager](certificate-infrastructure.md)  
> -   [Jak tworzyć profile certyfikatów w programie System Center Configuration Manager](create-certificate-profiles.md)    

> [!IMPORTANT]  
>  Po usunięciu wdrożenia profilu sieci VPN nie jest usuwany z urządzeń klientów. Aby usunąć profil z urządzeń, należy zrobić to ręcznie.
>   

## <a name="deploying--profiles"></a>Wdrażanie profilów  


1.  W konsoli programu System Center Configuration Manager wybierz **zasoby i zgodność**.  

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, rozwiń węzeł **dostęp do zasobów firmy**, a następnie wybierz typ odpowiedni profil, takich jak **profilów sieci Wi-Fi**.  

3.  Na liście profilów wybierz profil, który chcesz wdrożyć, a następnie w **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.  

4.  W oknie dialogowym wdrażania profilu Podaj następujące informacje:  

    -   **Kolekcja** — kliknij przycisk **Przeglądaj** aby wybrać kolekcję, w której chcesz wdrożyć profil.  

    -   **Generuj alert** — Włącz tę opcję skonfigurować alert generowany, jeżeli zgodność profilu jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

    -   -   **Opóźnienie losowe (godziny)**: (Tylko w przypadku profilów certyfikatów zawierających ustawienia prostego protokołu rejestrowania certyfikatów) Określa okno opóźnienia, aby uniknąć nadmiernego przetwarzania w usłudze rejestracji urządzeń sieciowych. Domyślna wartość to **64** godziny.  

    -   **Określ harmonogram oceny zgodności dla tego <type> profilu** — Określ harmonogram oceny wdrożonego profilu na komputerach klienckich. Harmonogram może być prosty lub niestandardowy.  

        > [!NOTE]  
        >  Klienci oceniają profile po zalogowaniu się użytkownika.  

5.  Kliknij przycisk **OK** aby zamknąć okno dialogowe i utworzyć wdrożenie.

### <a name="see-also"></a>Zobacz także  

[Monitorowanie sieci Wi-Fi, VPN i profile poczty e-mail w programie System Center Configuration Manager](monitor-wifi-email-vpn-profiles.md)

[Jak monitorować profile certyfikatów w programie System Center Configuration Manager](monitor-certificate-profiles.md)
