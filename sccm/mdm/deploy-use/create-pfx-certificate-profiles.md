---
title: "Tworzenie profilów certyfikatów PFX | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać plików PFX w programie System Center Configuration Manager do generowania certyfikatów specyficzne dla użytkownika, które obsługują zaszyfrowane dane programu exchange."
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
caps.latest.revision: 5
caps.handback.revision: 0
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 26feb0b166beb7e48cb800a5077d00dbc3eec51a
ms.openlocfilehash: 27435316c6e47531ff989bc8956ca0c874131a0e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-pfx-certificate-profiles-in-system-center-configuration-manager"></a>Tworzenie profilów certyfikatów PFX w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Profile certyfikatów pracować z usług certyfikatów w usłudze Active Directory i rolą usługi rejestracji urządzeń sieciowych, aby udostępnić certyfikaty uwierzytelniania dla zarządzanych urządzeń, dzięki czemu użytkownicy mogą uzyskiwanie dostępu do zasobów firmy. Można na przykład utworzyć i wdrożyć profile certyfikatów, aby udostępnić użytkownikom certyfikaty potrzebne do inicjowania połączeń VPN i bezprzewodowych.

[Profile certyfikatów](../../protect/deploy-use/introduction-to-certificate-profiles.md) zawiera ogólne informacje dotyczące tworzenia i konfigurowania profili certyfikatów. Ten temat prezentuje niektórych określonych informacji dotyczących profilów certyfikatów, dotyczące certyfikatów PFX.

-  Menedżer konfiguracji obsługuje wdrażanie certyfikatów do różnych magazynów certyfikatów, w zależności od wymogów, typu urządzenia i systemu operacyjnego. Po zarejestrowaniu w usłudze Intune obsługiwane są następujące urządzenia:

 -   iOS  

- Inne wymagania wstępne, można znaleźć w temacie [certyfikatu wymagania wstępne profilu](../../protect/plan-design/prerequisites-for-certificate-profiles.md).

## <a name="pfx-certificate-profiles"></a>Profile certyfikatów PFX
System Center Configuration Manager można zaimportować, a następnie udostępniać pliki programu exchange (pfx) informacji osobistych urządzeniach użytkownika. Pliki PFX mogą służyć do generowania certyfikatów specyficznych dla użytkownika w celu obsługi szyfrowanej wymiany danych.

> [!TIP]  
>  Przewodnik krok po kroku opisujący ten proces jest dostępny w temacie [Sposób tworzenia i wdrażania profilów certyfikatów PFX w programie Configuration Manager](http://blogs.technet.com/b/karanrustagi/archive/2015/09/01/how-to-create-and-deploy-pfx-certificate-profiles-in-configuration-manager.aspx).  

## <a name="create-and-deploy-a-personal-information-exchange-pfx-certificate-profile"></a>Tworzenie i wdrażanie profilu certyfikat wymiany informacji osobistych (PFX)  

### <a name="get-started"></a>Wprowadzenie

1.  W konsoli programu System Center Configuration Manager kliknij **zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń kategorię **Ustawienia zgodności**, rozwiń kategorię **Dostęp do zasobów firmy**, a następnie kliknij przycisk **Profile certyfikatów**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz profil certyfikatu**.

4.  Na stronie **Ogólne** kreatora **Tworzenie profilu certyfikatu** podaj następujące informacje:  

    -   **Nazwa**: Wprowadź unikatową nazwę profilu certyfikatu. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Opis**: Podaj opis, który umożliwia identyfikowanie profilu certyfikatu oraz inne istotne informacje ułatwiające identyfikację w konsoli programu System Center Configuration Manager. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Określ typ profilu certyfikatu, który chcesz utworzyć**: W przypadku certyfikatów PFX należy wybrać:  

        -   **Ustawienia osobiste wymiany informacji PKCS #12 (PFX) - Import**: Wybierz, aby zaimportować certyfikat z pliku PFX.  
       

### <a name="import-a-pfx-certificate"></a>Importowanie certyfikatu PFX

Aby zaimportować certyfikat z pliku PFX, należy zestaw SDK programu Configuration Manager. Wszystkie certyfikaty importowane dla użytkownika będzie wdrażany w żadnych urządzeń, które użytkownicy rejestrują się.

1. Na **certyfikat PFX** strony **Kreatora tworzenia profilu certyfikatu**, określ, gdzie będzie przechowywany certyfikat na urządzeniach, na których można wdrożyć:
    -     **Zainstaluj w module Trusted Platform Module (TPM), jeśli jest obecny**  
    -   **Zainstaluj w module Trusted Platform Module (TPM) albo zgłoś niepowodzenie** 
    -   **Zainstaluj Windows Hello dla firmy, w przeciwnym razie błąd** 
    -   **Zainstaluj u dostawcy magazynu kluczy oprogramowania** 
2. Kliknij przycisk **Dalej**. 
3. Na **obsługiwane platformy** strony kreatora wybierz platformy urządzeń, na których ten certyfikat zostanie zainstalowany, a następnie kliknij przycisk **dalej**.
4. Przeprowadź wdrożenie skryptu Create PFX Script, korzystając z zestawu SDK dla systemu Windows 8.1 dostępnego do pobrania z Centrum pobierania ([http://go.microsoft.com/fwlink/?LinkId=613525](http://go.microsoft.com/fwlink/?LinkId=613525)). Skrypt Create PFX Script dodany do programu Configuration Manager 2012 SP2 dodaje klasę SMS_ClientPfxCertificate do zestawu SDK. Ta klasa zawiera następujące metody:  

    -   ImportForUser  

    -   DeleteForUser  

     Przykładowy skrypt:  

```  
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

Na potrzeby Twojego skryptu następujące zmienne skryptu muszą zostać zmodyfikowane:  

   -   blob\ = obiektu blob PFX zaszyfrowane base64  
   -   $Password = hasło do pliku PFX  
   -   $ProfileName = nazwa profilu PFX  
   -   ComputerName = nazwa komputera hosta   



### <a name="finish-up"></a>Zakończ w

1.  Kliknij przycisk **Dalej**, przejrzyj stronę **Podsumowanie** , a następnie zamknij kreatora.  
2.  Po wykonaniu tych czynności profil certyfikatu zawierający plik PFX będzie dostępny w obszarze roboczym **Profile certyfikatu** . 
3.  Aby wdrożyć profil w **zasoby i zgodność** Otwórz obszar roboczy **ustawień zgodności** > **dostęp do zasobów firmy** > **profile certyfikatów**, kliknij prawym przyciskiem myszy certyfikat, a następnie kliknij przycisk **Wdróż**. 



## <a name="see-also"></a>Zobacz także
[Utwórz nowy profil certyfikatu](../../protect/deploy-use/create-certificate-profiles.md#create-a-new-certificate-profile) przeprowadzi Cię przez Kreatora tworzenia profilu certyfikatu.

[Wdrażanie sieci Wi-Fi, sieci VPN, profile certyfikatów oraz wiadomości e-mail](../../protect/deploy-use/deploy-wifi-vpn-email-cert-profiles.md) zawiera informacje dotyczące wdrażania profili certyfikatów.
