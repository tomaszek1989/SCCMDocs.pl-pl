---
title: "Tworzenie profilów certyfikatów PFX używany urząd certyfikacji | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak wykorzystywać pliki PFX w programie System Center Configuration Manager w celu wygenerowania certyfikatów specyficzne dla użytkownika, które obsługi wymiany zaszyfrowanych danych."
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d240a836-c49b-49ab-a920-784c062d6748
caps.latest.revision: "5"
caps.handback.revision: "0"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 43d8b2217763681be69711fce93c020a65da1cd8
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-create-pfx-certificate-profiles-using-a-certificate-authority"></a>Jak tworzyć profile certyfikatów PFX używany urząd certyfikacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym miejscu możesz Dowiedz się, jak utworzyć profil certyfikatu używanego przez urząd certyfikacji do poświadczeń.

[Profile certyfikatów](../../protect/deploy-use/introduction-to-certificate-profiles.md) zawiera ogólne informacje dotyczące tworzenia i konfigurowania profili certyfikatów. W tym temacie omówiono niektóre określone informacje o profilach certyfikatów związane z certyfikatów PFX.

## <a name="pfx-certificate-profiles"></a>Profile certyfikatów PFX
System Center Configuration Manager służy do tworzenia profilu certyfikatu PFX przy użyciu poświadczeń wystawiony przez urząd certyfikacji.  Począwszy od wersji 1706 można wybrać jako urzędu certyfikacji firmy Microsoft lub Entrust.  Po wdrożeniu urządzenia użytkowników, informacji osobistych (pfx) programu exchange pliki generowania certyfikatów specyficznych dla użytkownika w celu obsługi wymiany zaszyfrowanych danych.

Aby zaimportować certyfikat poświadczeń z istniejących plików certyfikatów, zobacz [jak tworzyć profile certyfikatów PFX importując szczegóły certyfikatu](../../mdm/deploy-use/import-pfx-certificate-profiles.md).

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Tworzenie i wdrażanie profilów certyfikatów wymiany informacji osobistych (PFX)  

### <a name="get-started"></a>Wprowadzenie

1.  W konsoli programu System Center Configuration Manager wybierz **zasoby i zgodność**.  
2.  W **zasoby i zgodność** obszaru roboczego wybierz **ustawień zgodności** &gt; **dostęp do zasobów firmy** &gt; **profilów certyfikatów**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Tworzenie profilu certyfikatu**.

4.  Na stronie **Ogólne** kreatora **Tworzenie profilu certyfikatu** podaj następujące informacje:  

    -   **Nazwa**: Wprowadź unikatową nazwę profilu certyfikatu. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Opis elementu**: Podaj opis, który umożliwia identyfikowanie profilu certyfikatu oraz inne istotne informacje ułatwiające znalezienie go w konsoli programu System Center Configuration Manager. Możesz wprowadzić maksymalnie 256 znaków.  

    -   W **Określ typ profilu certyfikatu, który chcesz utworzyć**, wybierz **wymiany informacji osobistych — ustawienia PKCS #12 (PFX) — tworzenie** , a następnie wybierz z listy rozwijanej urzędu certyfikacji.  Począwszy od wersji 1706, może wybrać **Microsoft** lub **Entrust**.

### <a name="select-supported-platforms"></a>Wybierz obsługiwane platformy

Na stronie obsługiwane platformy identyfikuje systemami operacyjnymi i urządzeniami, które są obsługiwane przez profil certyfikatu.  

Certyfikatów, profile może obsługiwać wiele systemami operacyjnymi i urządzeniami, jednak, niektórych systemu operacyjnego lub kombinacji urządzeń mogą wymagać różnych ustawień.  W takich przypadkach najlepiej utworzyć osobnych profilów dla każdego unikatowego zestawu ustawień.  

Począwszy od wersji 1706 dostępne są następujące opcje:

- Windows 10
    - Wszystkie Windows 10 (wersja 64-bitowa)
    - Wszystkie Windows 10 (wersja 32-bitowa)
    - Wszystkie systemy Windows 10 Holographic Enterprise i nowsze
    - Wszystkie systemy Windows 10 Holographic i nowsze
    - Wszystkie systemy Windows 10 Team i nowsze
    - Wszystkie systemy Windows 10 Mobile i nowsze
- urządzenia iPhone
- iPad
- Android
- Android for Work

> [!Note]  
> System MacOS/OS x urządzenia nie są obecnie obsługiwane.  

Jeśli nie wybrano żadnych innych opcji, **Zaznacz wszystko** wyboru wybiera wszystkich dostępnych opcji.  Po wybraniu co najmniej jedna opcja, **Zaznacz wszystko** spowoduje wyczyszczenie istniejących zaznaczeń. 

1.  Wybierz co najmniej jedną platformę obsługiwane przez profil certyfikatu.

1.  Wybierz **dalej** aby kontynuować.  


### <a name="configure-certification-authorities"></a>Konfigurowanie urzędów certyfikacji

W tym miejscu wybierzesz punkt rejestracji certyfikatu (CRP), aby przetworzyć certyfikatów PFX.  

1.  Z **lokacji głównej** listy, wybierz serwer zawierający CRP rolę urzędu certyfikacji.
1.  Z listy **urzędów certyfikacji**, wybierz odpowiedniego urzędu certyfikacji, umieszczając znacznik wyboru w kolumnie po lewej stronie.
1.  Po wykonaniu tych czynności kontynuować, wybierz **dalej**.

Aby dowiedzieć się więcej, zobacz [infrastruktury certyfikatów](../../protect/deploy-use/certificate-infrastructure.md).


### <a name="configure-certificate-settings-for-microsoft-ca"></a>Konfigurowanie ustawień certyfikatów dla urzędu certyfikacji firmy Microsoft

Aby skonfigurować ustawienia certyfikatu, używając jako urzędu certyfikacji firmy Microsoft:

1.  Z **nazwę szablonu certyfikatu** listy rozwijanej, wybierz szablon certyfikatu.

1.  Włącz **zastosowanie certyfikatów** pole wyboru, aby użyć profilu certyfikatu do szyfrowania S/MIME podpisywania lub szyfrowania.

    Po zaznaczeniu tej opcji podczas korzystania z urzędu certyfikacji firmy Microsoft, wszystkie certyfikaty PFX skojarzony z użytkownikiem docelowego są dostarczane do wszystkich urządzeń zarejestrowanych przez użytkownika.  Gdy to pole wyboru jest zaznaczone, każde urządzenie otrzymuje unikatowy certyfikat.  

1.  Ustaw **format nazwy podmiotu** albo **nazwa pospolita** lub **nazwę wyróżniającą pełni**.  Jeśli nie wiesz, których chcesz użyć, skontaktuj się z administratorem urzędu certyfikatu.

1.  Dla **alternatywnej nazwy podmiotu**, Włącz **adres E-mail** i **główna nazwa użytkownika (UPN)** odpowiednio dla urzędu certyfikacji.

1.  **Próg odnawiania** Określa, kiedy certyfikaty są automatycznie odnawiane, na podstawie procentu czasu pozostałego do wygaśnięcia.

1.  Ustaw **okres ważności certyfikatu** na okres istnienia certyfikatu.  Okres jest określany przez ustawienie numer (1-100) i okres (lat, miesięcy lub dni).

1.  **Publikowania usługi Active Directory** jest włączona, gdy punkt rejestracji certyfikatu określa poświadczenia usługi Active Directory.  Włącz opcję, aby opublikować profilu certyfikatu w usłudze Active Directory.

1.  Jeśli wybrano co najmniej jedną platformę systemu Windows 10, określając obsługiwane platformy:

    1.  Ustaw **magazynu certyfikatów systemu Windows** do **użytkownika**.  ( **Komputera lokalnego** wyboru nie wdrażanie certyfikatów i nie należy wybierać.)
    1.  Wybierz **dostawcy magazynu kluczy (KSP)** jedną z następujących opcji:

        - **Zainstaluj w module Trusted Platform Module (TPM), jeśli jest obecny**  
        - **Zainstaluj w module Trusted Platform Module (TPM) albo zgłoś niepowodzenie** 
        - **Zainstaluj w usłudze Windows Hello for Business, w przeciwnym razie błąd** 
        - **Zainstaluj u dostawcy magazynu kluczy oprogramowania** 

1.  Po zakończeniu wybierz **dalej** lub **Podsumowanie**.

### <a name="configure-certificate-settings-for-entrust-ca"></a>Konfigurowanie ustawień certyfikatów dla urzędu certyfikacji Entrust

Aby skonfigurować ustawienia certyfikatu, używając powierzyć jako urzędu certyfikacji:

1.  Z **konfiguracji identyfikator cyfrowy** listy rozwijanej, wybierz profil konfiguracji.  Opcje konfiguracji identyfikator cyfrowy są tworzone przez administratora Entrust.

1.  Po zaznaczeniu tej opcji, **zastosowanie certyfikatów** korzysta z profilu certyfikatu do szyfrowania S/MIME podpisywania lub szyfrowania.

    Korzystając z Entrust jako urząd certyfikacji, wszystkie certyfikaty PFX skojarzony z użytkownikiem docelowego są dostarczane do wszystkich urządzeń zarejestrowanych przez użytkownika.    Gdy ta opcja jest *nie* zaznaczone, każde urządzenie otrzymuje unikatowy certyfikat.  (Zachowanie zmienia się na inne urzędy certyfikacji; Aby dowiedzieć się więcej, zobacz odpowiedniej sekcji).

1.  Użyj **Format** przycisk, aby mapować Entrust **format nazwy podmiotu** tokenów do pól programu ConfigMgr.  

    **Formatowanie nazwy certyfikatu** zmienne konfiguracji powierzyć identyfikator cyfrowy Wyświetla okno dialogowe.  Dla każdej zmiennej Entrust wybierz odpowiednią zmienną LDAP ze skojarzonej listy rozwijanej.

1.  Użyj **Format** przycisk, aby mapować Entrust **alternatywna nazwa podmiotu** tokenów do obsługiwanych zmiennych LDAP.  

    **Formatowanie nazwy certyfikatu** zmienne konfiguracji powierzyć identyfikator cyfrowy Wyświetla okno dialogowe.  Dla każdej zmiennej Entrust wybierz odpowiednią zmienną LDAP ze skojarzonej listy rozwijanej.

1.  **Próg odnawiania** Określa, kiedy certyfikaty są automatycznie odnawiane, na podstawie procentu czasu pozostałego do wygaśnięcia.

1.  Ustaw **okres ważności certyfikatu** na okres istnienia certyfikatu.  Okres jest określany przez ustawienie numer (1-100) i okres (lat, miesięcy lub dni).

1.  **Publikowania usługi Active Directory** jest włączona, gdy punkt rejestracji certyfikatu określa poświadczenia usługi Active Directory.  Włącz opcję, aby opublikować profilu certyfikatu w usłudze Active Directory.

1.  Jeśli wybrano co najmniej jedną platformę systemu Windows 10, określając obsługiwane platformy:

    1.  Ustaw **magazynu certyfikatów systemu Windows** do **użytkownika**.  ( **Komputera lokalnego** wyboru nie wdrażanie certyfikatów i nie należy wybierać.)
    1.  Wybierz **dostawcy magazynu kluczy (KSP)** jedną z następujących opcji:

        - **Zainstaluj w module Trusted Platform Module (TPM), jeśli jest obecny**  
        - **Zainstaluj w module Trusted Platform Module (TPM) albo zgłoś niepowodzenie** 
        - **Zainstaluj w usłudze Windows Hello for Business, w przeciwnym razie błąd** 
        - **Zainstaluj u dostawcy magazynu kluczy oprogramowania** 

1.  Po zakończeniu wybierz **dalej** lub **Podsumowanie**.


### <a name="finish-up"></a>Aby zakończyć

1.  Na stronie Podsumowanie przejrzyj wybrane opcje, a następnie sprawdź wybrane opcje.

1.  Po wykonaniu tych czynności wybierz **dalej** do tworzenia profilu.  

1.  Po wykonaniu tych czynności profil certyfikatu zawierający plik PFX będzie dostępny w obszarze roboczym **Profile certyfikatu** . 

1.  Aby wdrożyć profil:

    1. Otwórz **zasoby i zgodność** obszaru roboczego.
    1. Wybierz **ustawień zgodności** > **dostęp do zasobów firmy** > **profile certyfikatów**
    1. Kliknij prawym przyciskiem myszy profil żądanego certyfikatu, a następnie wybierz pozycję **Wdróż**. 


## <a name="see-also"></a>Zobacz także
[Utwórz nowy profil certyfikatu](../../protect/deploy-use/create-certificate-profiles.md) przeprowadzi Cię przez Kreatora tworzenia profilu certyfikatu.

[Jak tworzyć profile certyfikatów PFX importując szczegóły certyfikatu](../../mdm/deploy-use/import-pfx-certificate-profiles.md)

[Wdrażanie sieci Wi-Fi, VPN, poczty e-mail i profilów certyfikatów](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) opisano sposób wdrażania profili certyfikatów.