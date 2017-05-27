---
title: "Windows Hello ustawień biznesowych | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak integrować Windows Hello dla firm z System Center Configuration Manager."
ms.custom: na
ms.date: 04/25/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a95bc292-af10-4beb-ab56-2a815fc69304
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 699b79b68440b61904a9053e5004318a2a248bfd
ms.openlocfilehash: 75def95561feb35f2f060f0daa72291983324d4f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="windows-hello-for-business-settings-in-system-center-configuration-manager"></a>Ustawienia funkcji Windows Hello dla firm w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager umożliwia integrację z Windows Hello dla firm (dawniej Passport firmy Microsoft dla systemu Windows), który jest alternatywna metoda logowania dla urządzeń z systemem Windows 10. Funkcja Hello dla firm korzysta z usługi Active Directory lub konta usługi Azure Active Directory w celu zastąpienia hasła, karty inteligentnej lub wirtualnej karty inteligentnej.  

Funkcja Hello dla firm pozwala używać **gestu użytkownika** do logowania, zamiast hasła. Gestem użytkownika może być prosty numer PIN, uwierzytelnianie biometryczne lub urządzenie zewnętrzne, np. czytnik linii papilarnych.

[Dowiedz się więcej o Windows Hello dla firm](https://docs.microsoft.com/windows/access-protection/hello-for-business/hello-identity-verification)

 Menedżer konfiguracji integruje się z systemu Windows Hello dla firm na dwa sposoby:  

-   Aby kontrolować, którzy użytkownicy gestów mogą i nie można używać do logowania, można użyć programu Configuration Manager.  

-   W dostawcy magazynu kluczy funkcji Windows Hello dla firm można przechowywać certyfikaty uwierzytelniania. Aby uzyskać więcej informacji, zobacz [profile certyfikatów](introduction-to-certificate-profiles.md).  

- Można wdrożyć Windows Hello zasady biznesowe przyłączonych do domeny systemu Windows 10 urządzeń, które Uruchom klienta programu Configuration Manager. Ta konfiguracja jest opisany w [skonfigurować Windows Hello firmy na urządzeniach przyłączonych do domeny systemu Windows 10](#configure-windows-hello-for-business-on-domain-joined-windows-10-devices), poniżej. Używając programu Configuration Manager za pomocą usługi Intune (hybrydowy), te ustawienia można skonfigurować w Windows 10 i Windows 10 Mobile urządzeń, ale nie w urządzeń dołączonych do domeny, które Uruchom klienta programu Configuration Manager. Zobacz [skonfigurować Windows Hello dla firm ustawienia (hybrydowy)](../../mdm/deploy-use/windows-hello-for-business-settings.md) uzyskać więcej informacji.

## <a name="configure-windows-hello-for-business-on-domain-joined-windows-10-devices"></a>Konfigurowanie systemu Windows Hello dla firm na urządzeniach przyłączonych do domeny systemu Windows 10
Można kontrolować Windows Hello ustawień biznesowych na przyłączonych do domeny systemu Windows 10 urządzeń na trzy sposoby:

- Można utworzyć i wdrożyć system Windows Hello profilu biznesowych. Jest to zalecane podejście.
- Można użyć zasad grupy.  
- Można użyć skryptu programu PowerShell.

Należy zauważyć że oprócz tej konfiguracji należy również wdrożyć profil certyfikatu, zgodnie z opisem w [konfiguracji profilu certyfikatu](#configure-a-certificate-profile).

## <a name="configure-a-windows-hello-for-business-profile"></a>Konfigurowanie systemu Windows Hello profilu biznesowe  

W konsoli programu Configuration Manager w obszarze **dostęp do zasobów firmy**, kliknij prawym przyciskiem myszy **Windows Hello profilów Business** i wybierz polecenie **New** Aby uruchomić Kreatora profilu. Podaj ustawienia wymagane przez kreatora, przejrzyj i Potwierdź ustawienia na ostatniej stronie, a następnie kliknij przycisk **Zamknij**. Oto przykład jak może wyglądać ustawień:  

![Ustawienia funkcji Windows Hello dla firm](../media/Hello-for-Business-settings.png)

## <a name="configure-windows-hello-for-business-with-group-policy-in-active-directory"></a>Konfigurowanie systemu Windows Hello dla firm za pomocą zasad grupy w usłudze Active Directory  

Zasad grupy usługi Active Directory umożliwia konfigurowanie urządzeń przyłączonych do domeny systemu Windows 10 do udostępniania użytkownika Hello biznesowych poświadczeń podczas logowania do systemu Windows:

1.  Na komputerze serwera systemu Windows, otwórz Menedżera serwera, a następnie przejdź do **narzędzia** > **Zarządzanie zasadami grupy**.    

2.  W **Zarządzanie zasadami grupy** okna dialogowego rozwiń domenę, w której chcesz włączyć automatyczne Dołącz do miejsca pracy.    

3.  Kliknij prawym przyciskiem myszy **obiekty zasad grupy**, a następnie kliknij przycisk **nowy**.  

4.  W **nowego obiektu zasad grupy** okna dialogowego wprowadź nazwę dla nowego obiektu zasad grupy, takie jak **włączyć Windows Hello dla firm**, a następnie kliknij przycisk **OK**.  

5.  W **obiekty zasad grupy** węzła, kliknij prawym przyciskiem myszy obiekt został właśnie utworzony, a następnie kliknij przycisk **edytować**.  

6.  W **Edytor zarządzania zasadami grupy** okna dialogowego, przejdź do **konfiguracji komputera** > **zasad** > **Szablony administracyjne** > **składniki systemu Windows** > **Windows Hello dla firm**.  

7.  Kliknij prawym przyciskiem myszy **włączyć Windows Hello dla firm** , a następnie kliknij przycisk **edytować**.   

8.  Wybierz **włączone**, kliknij przycisk **Zastosuj**, a następnie kliknij przycisk **OK**.

Teraz możesz połączyć utworzonego obiektu zasad grupy do wybranej lokalizacji. Na przykład:    

   Określone organizacyjne jednostki (OU) w AD, w którym będzie umieszczona komputerów przyłączonych do domeny systemu Windows 10.    

   Grupa zabezpieczeń obejmująca przyłączonych do domeny komputery Windows 10, które zostanie automatycznie zarejestrowany z usługą Azure AD.    

## <a name="configure-windows-hello-for-business-by-deploying-a-powershell-script-with-configuration-manager"></a>Konfigurowanie systemu Windows Hello dla firm przez wdrożenie skryptu PowerShell z programu Configuration Manager    
Można tworzyć i wdrażać poniższy skrypt programu PowerShell za pomocą zarządzania aplikacjami programu Configuration Manager.    

Obejście - ExecutionPolicy **PowerShell.exe - NoLogo - NoProfile — polecenia "& {nowe-zmieniona właściwość elementu"HKLM:\Software\Policies\Microsoft\PassportForWork"— Nazwa"Enabled"-"DWord"wartość 1 - elementu PropertyType-Force}" ** 

Aby uzyskać więcej informacji dotyczących zarządzania aplikacjami programu Configuration Manager, zobacz [wprowadzenie do zarządzania aplikacjami w programie System Center Configuration Manager](/sccm/apps/understand/introduction-to-application-management).  

## <a name="configure-a-certificate-profile-to-enroll-the-windows-hello-for-business-enrollment-certificate-in-configuration-manager"></a>Konfigurowanie profilu certyfikatu w celu zarejestrowania certyfikatu rejestracji funkcji Windows Hello dla firm w programie Configuration Manager  
 Jeśli chcesz użyć opartego na certyfikatach logowania do funkcji Windows Hello dla firm lub usługi Microsoft Hello, skonfiguruj następujące elementy:  

-   Menedżer konfiguracji profilu certyfikatu.  

-   W profilu certyfikatu wybierz szablon korzystający z rozszerzonego użycia klucza Logowanie karty inteligentnej.  

-    Jeśli planujesz przechowywać profili certyfikatów w Windows Hello dla kontenera kluczy biznesowych i korzysta z profilu certyfikatu **logowania karty inteligentnej** EKU, należy skonfigurować następujące uprawnienia do klucza rejestracji w celu zapewnienia, certyfikat zostanie zweryfikowany poprawnie.
Najpierw należy utworzyć **Administratorzy klucz** grupy i dodać wszystkie programu Configuration Manager punkt zarządzania komputerami jako członków do tej grupy.

    1.    Zaloguj się do kontrolera lub zarządzania stacjach roboczych z administratora domeny lub równoważne poświadczeń.
    2.    Otwórz **komputerów i użytkowników usługi Active Directory**.
    3.    W okienku nawigacji kliknij prawym przyciskiem myszy nazwę domeny, a następnie kliknij przycisk **właściwości**.
    4.    Na **zabezpieczeń** na karcie  *<domain name>*  **właściwości** okno dialogowe, kliknij przycisk **zaawansowane**. Jeśli **zabezpieczeń** karta nie jest wyświetlana, należy włączyć funkcję **funkcje zaawansowane** z **widoku** menu **użytkownicy usługi Active Directory i komputerów**.
    5.    Kliknij pozycję **Dodaj**.
    6.    W **wpis uprawnienia dla**  *<domain name>*  okno dialogowe, kliknij przycisk **wybierz nazwę główną**.
    7.    W **wybierz użytkownika, komputera, konto usługi lub grupy** okno dialogowe, typ **Administratorzy klucz** w **wprowadź nazwę obiektu do wybrania** pola tekstowego.  Kliknij przycisk **OK**.
    8.    Z **dotyczą** listy wybierz **obiekty użytkownika obiekt podrzędny**.
    9.    Przewiń w dół strony i kliknij przycisk **wyczyść wszystkie**.
    10.    W **właściwości** zaznacz **odczytać msDS-KeyCredentialLink**.
    11.    Kliknij przycisk **OK** trzy razy, aby ukończyć zadanie.


 Aby uzyskać więcej informacji, zobacz [profile certyfikatów](introduction-to-certificate-profiles.md).  





