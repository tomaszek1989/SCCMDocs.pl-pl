---
title: "Usługi Windows Hello dla firm ustawienia | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zintegrować Windows Hello dla firm z System Center Configuration Manager."
ms.custom: na
ms.date: 09/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: "17"
author: lleonard-msft
ms.author: alleonar
manager: angrobe
ms.openlocfilehash: 43586e55f2c0c5cf117b94c61250f26ba4233f53
ms.sourcegitcommit: 4c3906cf9614420cb8527da9e48978eb0b8f0e7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2017
---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>Ustawienia funkcji Windows Hello dla firm w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager umożliwia integrację z usługą Windows Hello dla firm (dawniej Microsoft Passport dla systemu Windows), czyli alternatywną metodą logowania dla urządzeń z systemem Windows 10. Funkcja Hello dla firm korzysta z usługi Active Directory lub konta usługi Azure Active Directory w celu zastąpienia hasła, karty inteligentnej lub wirtualnej karty inteligentnej.  

Funkcja Hello dla firm pozwala używać **gestu użytkownika** do logowania, zamiast hasła. Gestem użytkownika może być prosty numer PIN, uwierzytelnianie biometryczne lub urządzenie zewnętrzne, np. czytnik linii papilarnych.

[Dowiedz się więcej na temat usługi Windows Hello dla firm](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification)

 Configuration Manager integruje się z usługi Windows Hello dla firm na dwa sposoby:  

-   Aby kontrolować gesty użytkownicy mogą i nie można używać do logowania, można użyć programu Configuration Manager.  

-   W dostawcy magazynu kluczy funkcji Windows Hello dla firm można przechowywać certyfikaty uwierzytelniania. Aby uzyskać więcej informacji, zobacz [profile certyfikatów](introduction-to-certificate-profiles.md).  

- Można wdrożyć usługi Windows Hello dla firm zasad na urządzeniach przyłączonych do domeny systemu Windows 10, w z klientem programu Configuration Manager. Ta konfiguracja jest opisana w [konfigurowania usługi Windows Hello dla firm na urządzeniach z systemem Windows 10 przyłączonych do domeny](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices), poniżej. Gdy używasz programu Configuration Manager w usłudze Microsoft Intune (rozwiązanie hybrydowe), te ustawienia można skonfigurować na systemu Windows 10 i urządzeniach z systemem Windows 10 Mobile. Zobacz [konfigurowania usługi Windows Hello dla firm ustawienia (rozwiązanie hybrydowe)](../../mdm/deploy-use/windows-hello-for-business-settings.md) Aby uzyskać więcej informacji.

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>Konfigurowanie usługi Windows Hello dla firm na urządzeniach z systemem Windows 10 przyłączonych do domeny
Można kontrolować Windows Hello dla firm ustawień na urządzeniach z systemem Windows 10 przyłączonych do domeny, tworząc i wdrażając Windows Hello dla firm. Jest to zalecane podejście.


Jeśli korzystasz z uwierzytelniania opartego na certyfikatach, należy również wdrożyć profil certyfikatu zgodnie z opisem w [konfiguracji profilu certyfikatu](#configure-a-certificate-profile). Jeśli korzystasz z uwierzytelniania opartego na kluczach, Wdróż profil certyfikatu nie jest konieczne.

## <a name="configure-a-windows-hello-for-business-profile"></a>Konfigurowanie usługi Windows Hello dla firm  

W konsoli programu Configuration Manager w obszarze **dostęp do zasobów firmy**, kliknij prawym przyciskiem myszy **usługi Windows Hello dla firm profile** i wybierz polecenie **nowy** Aby uruchomić Kreatora profilu. Podaj ustawienia wymagane przez kreatora, przejrzyj i Potwierdź ustawienia na ostatniej stronie, a następnie kliknij przycisk **Zamknij**. Oto przykład jak może wyglądać ustawienia:  

![Ustawienia funkcji Windows Hello dla firm](../media/Hello-for-Business-settings.png)

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Konfigurowanie profilu certyfikatu w celu zarejestrowania certyfikatu rejestracji funkcji Windows Hello dla firm w programie Configuration Manager  
 Jeśli chcesz użyć usługi Windows Hello dla firm oparte na certyfikatach logowania, skonfiguruj następujące ustawienia:  

-   Profil certyfikatu programu Configuration Manager.  

-   W profilu certyfikatu wybierz szablon korzystający z rozszerzonego użycia klucza Logowanie karty inteligentnej.  

-   Jeśli chcesz przechowywać profilów certyfikatów w usługi Windows Hello dla firm kontenera kluczy i korzysta z profilu certyfikatu **Logowanie karty inteligentnej** EKU, należy skonfigurować następujące uprawnienia do klucza rejestracji upewnić się, certyfikat zostanie zweryfikowany poprawnie.
Najpierw należy utworzyć **Administratorzy klucz** grupy i dodać wszystkie programu Configuration Manager punkt zarządzania komputerami jako członków do tej grupy.

Niektóre konfiguracje nie może być konieczne można skonfigurować uprawnienia lub mogą wymagać dalszej konfiguracji. Można skorzystać z poniższej tabeli, aby uzyskać więcej informacji:

|||||
|-|-|-|-|
|Wersja klienta systemu Windows|Configuration Manager 1602 lub 1606|Menedżer konfiguracji 1610|Menedżer konfiguracji 1702 lub nowszy|
|Windows 10 Anniversary aktualizacji|Wymagana poprawka<br><br>Brak wymaganych uprawnień<br><br>Wymagana aktualizacja schematu systemu Windows|Wymagana poprawka (zobacz **ostrzeżenie**)<br><br>Brak wymaganych uprawnień<br><br>Wymagana aktualizacja schematu systemu Windows|Konfigurowanie uprawnień<br><br>Dotyczy systemu Windows Server 2016 schematu usługi Active Directory|
|Windows 10 twórców Update lub nowszy|Nieobsługiwane|Zainstaluj [tej poprawki](https://support.microsoft.com/help/4010155/update-rollup-for-system-center-configuration-manager-current-branch-v)<br><br>Konfigurowanie uprawnień<br><br>Dotyczy systemu Windows Server 2016 schematu usługi Active Directory|Konfigurowanie uprawnień<br><br>Dotyczy systemu Windows Server 2016 schematu usługi Active Directory|

> [!WARNING]
> Gdy [poprawkę](https://support.microsoft.com/help/4010155/update-rollup-for-system-center-configuration-manager-current-branch-v) jest nie wymaga 1610 Menedżera konfiguracji i Windows 10 Anniversary Update, mógł zostać zainstalowany.  Po zainstalowaniu poprawki należy skonfigurować uprawnienia i dotyczą systemu Windows Server 2016 schematu usługi Active Directory.

## <a name="to-configure-permissions"></a>Aby skonfigurować uprawnienia

1.  Zaloguj się do kontrolera lub zarządzania stacjach roboczych z administratora domeny lub równoważne poświadczeń.
2.  Otwórz **użytkowników usługi Active Directory i komputery**.
3.  W okienku nawigacji kliknij prawym przyciskiem myszy nazwę domeny, a następnie kliknij przycisk **właściwości**.
4.  Na **zabezpieczeń** karcie * <domain name> * **właściwości** okno dialogowe, kliknij przycisk **zaawansowane**. Jeśli **zabezpieczeń** karta nie jest wyświetlana, Włącz **funkcje zaawansowane** z **widoku** menu **użytkownicy usługi Active Directory i komputery**.
5.  Kliknij pozycję **Dodaj**.
6.  W **wpis uprawnienia dla** * <domain name> * okno dialogowe, kliknij przycisk **Wybierz podmiot zabezpieczeń**.
7.  W **wybierz użytkownika, komputera, konto usługi lub grupy** okno dialogowe, typ **Administratorzy klucza** w **wprowadź nazwę obiektu do wybrania** pola tekstowego.  Kliknij przycisk **OK**.
8.  Z **dotyczy** listy, wybierz **obiekty użytkownika podrzędnym**.
9.  Przewiń do dołu strony, a następnie kliknij przycisk **Wyczyść wszystko**.
10. W **właściwości** zaznacz **odczytu msDS-KeyCredentialLink**.
11. Kliknij przycisk **OK** trzy razy, aby ukończyć zadanie.


## <a name="next-steps"></a>Następne kroki

Aby uzyskać więcej informacji, zobacz [profile certyfikatów](introduction-to-certificate-profiles.md).  




