---
title: "Tworzenie profilów certyfikatów PFX importując szczegóły certyfikatu"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak wykorzystywać pliki PFX w programie System Center Configuration Manager w celu wygenerowania certyfikatów specyficzne dla użytkownika, które obsługi wymiany zaszyfrowanych danych."
ms.custom: na
ms.date: 04/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e3bb3e13-3037-4122-93bc-504bfd080a4d
caps.latest.revision: 
caps.handback.revision: 
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 25c6927698e409ff3b0c3f846e2cc567a6f458ab
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-pfx-certificate-profiles-by-importing-certificate-details"></a>Jak tworzyć profile certyfikatów PFX importując szczegóły certyfikatu

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


W tym miejscu możesz Dowiedz się, jak utworzyć profil certyfikatu przez zaimportowanie poświadczenia z certyfikatów zewnętrznych.  

[Profile certyfikatów](../../protect/deploy-use/introduction-to-certificate-profiles.md) zawierają ogólne informacje dotyczące tworzenia i konfigurowania profili certyfikatów. W tym temacie omówiono niektóre określone informacje o profilach certyfikatów związane z certyfikatów PFX.

-  Menedżer konfiguracji różnych magazynów certyfikatów, które są odpowiednie dla różnych urządzeń i systemów operacyjnych.  Należą do nich następujące elementy:

 -   iOS i MacOS/OS x
 -   Android i Android for Work
 -   Windows 10, w tym Windows 10 mobile.

Aby dowiedzieć się więcej, zobacz [wymagania wstępne dotyczące profilów certyfikatów](../../protect/plan-design/prerequisites-for-certificate-profiles.md).

## <a name="pfx-certificate-profiles"></a>Profile certyfikatów PFX
System Center Configuration Manager umożliwia importowanie certyfikatów poświadczenia, a następnie zainicjujesz informacji osobistych (pfx) programu exchange plików na urządzeniach użytkownika. Pliki PFX mogą służyć do generowania certyfikatów specyficznych dla użytkownika w celu obsługi szyfrowanej wymiany danych.

> [!TIP]  
>  Przewodnik krok po kroku opisujący ten proces jest dostępny w temacie [Sposób tworzenia i wdrażania profilów certyfikatów PFX w programie Configuration Manager](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx).  

## <a name="create-import-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Tworzenie, importowanie i wdrażanie profilów certyfikatów wymiany informacji osobistych (PFX)  

### <a name="get-started"></a>Wprowadzenie

1.  W konsoli programu System Center Configuration Manager kliknij **zasoby i zgodność**.  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń kategorię **Ustawienia zgodności**, rozwiń kategorię **Dostęp do zasobów firmy**, a następnie kliknij przycisk **Profile certyfikatów**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz profil certyfikatu**.

4.  Na stronie **Ogólne** kreatora **Tworzenie profilu certyfikatu** podaj następujące informacje:  

    -   **Nazwa**: Wprowadź unikatową nazwę profilu certyfikatu. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Opis elementu**: Podaj opis, który umożliwia identyfikowanie profilu certyfikatu oraz inne istotne informacje ułatwiające znalezienie go w konsoli programu System Center Configuration Manager. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Określ typ profilu certyfikatu, który chcesz utworzyć**: Certyfikaty PFX wybierz jedną z następujących opcji:  

        -   **Ustawienia osobiste informacje Exchange PKCS #12 (PFX) — Import**: Tworzy profil certyfikatu programowo importując informacje z istniejących certyfikatów.  

        -   **Wymiana informacji osobistych — ustawienia PKCS #12 (PFX) — tworzenie**: Tworzy profil certyfikatu PFX, używając poświadczeń dostarczonych przez urząd certyfikacji.  Aby dowiedzieć się więcej, zobacz [jak tworzyć profile certyfikatów PFX używany urząd certyfikacji](../../mdm/deploy-use/create-pfx-certificate-profiles.md).


### <a name="create-a-pfx-certificate-profile-for-the-imported-credentials"></a>Utwórz profil certyfikatu PFX dla importowanych poświadczeń

Aby zaimportować certyfikat PFX, zestaw SDK programu Configuration Manager służy do wdrożenia skryptu Utwórz PFX. 

Zaimportowane certyfikaty później są wdrażane do zarejestrowanych urządzeń.

1. Na **certyfikatu PFX** strony **Kreatora tworzenia profilu certyfikatu**, określ, w którym urządzenie klucza dostawcy magazynu:
    -   **Zainstaluj w module Trusted Platform Module (TPM), jeśli jest obecny**  
    -   **Zainstaluj w module Trusted Platform Module (TPM) albo zgłoś niepowodzenie** 
    -   **Zainstaluj w usłudze Windows Hello for Business, w przeciwnym razie błąd** 
    -   **Zainstaluj u dostawcy magazynu kluczy oprogramowania** 
2. Kliknij przycisk **Dalej**. 
3. Na **obsługiwane platformy** strony kreatora wybierz platformy obsługiwanych urządzeń, a następnie kliknij przycisk **dalej**.

### <a name="finish-the-profile"></a>Zakończ profilu

1.  Kliknij przycisk **Dalej**, przejrzyj stronę **Podsumowanie** , a następnie zamknij kreatora.  
2.  Po wykonaniu tych czynności profil certyfikatu zawierający plik PFX będzie dostępny w obszarze roboczym **Profile certyfikatu** . 
3.  Aby wdrożyć profil, w **zasoby i zgodność** Otwórz obszar roboczy **ustawień zgodności** > **dostęp do zasobów firmy** > **profilów certyfikatów**, kliknij prawym przyciskiem myszy certyfikat, a następnie kliknij przycisk **Wdróż**. 

### <a name="deploy-a-create-pfx-script"></a>Wdrażanie utworzyć skrypt PFX

Użyj [zestawu SDK programu Configuration Manager](http://go.microsoft.com/fwlink/?LinkId=613525) do wdrożenia skryptu Create PFX Script. 

Skrypt Create PFX Script dodany do programu Configuration Manager 2012 SP2 dodaje klasę SMS_ClientPfxCertificate do zestawu SDK. Ta klasa zawiera następujące metody:  

    -   `ImportForUser`  

    -   `DeleteForUser`  

Poniższy przykład importuje poświadczenia do profilu certyfikatu PFX.

``` powershell
    $EncryptedPfxBlob = "<blob>"  
    $Password = "abc"  
    $ProfileName = "PFX_Profile_Name"  
    $UserName = "ComputerName\Administrator"  

    #New pfx  
    $WMIConnection = ([WMIClass]"\\nksccm\root\SMS\Site_MDM:SMS_ClientPfxCertificate")  
        $NewEntry = $WMIConnection.psbase.GetMethodParameters("ImportForUser")  
        $NewEntry.EncryptedPfxBlob = $EncryptedPfxBlob  
        $NewEntry.Password = $Password  
        $NewEntry.ProfileName = $ProfileName  
        $NewEntry.UserName = $UserName  
    $Resource = $WMIConnection.psbase.InvokeMethod("ImportForUser",$NewEntry,$null)  
```  

Aby użyć tego przykładu, należy zaktualizować następujące zmienne skryptu:  

   -   **Obiekt blob**\ — obiektu blob PFX base64 systemu szyfrowania plików  
   -   **$Password** — hasło do pliku PFX  
   -   **$ProfileName** — nazwa profilu PFX  
   -   **ComputerName** — nazwa komputera hosta   

## <a name="see-also"></a>Zobacz także
[Utwórz nowy profil certyfikatu](../../protect/deploy-use/create-certificate-profiles.md) przeprowadzi Cię przez Kreatora tworzenia profilu certyfikatu.

[Jak tworzyć profile certyfikatów PFX importując szczegóły certyfikatu](../../mdm/deploy-use/create-pfx-certificate-profiles.md)

[Wdrażanie sieci Wi-Fi, VPN, poczty e-mail i profilów certyfikatów](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) opisuje Pokaż do wdrażania profili certyfikatów.