---
title: "Konfigurowanie hybrydowego zarządzania urządzeniami z systemem Windows usłudze Microsoft Intune"
titleSuffix: Configuration Manager
description: "Konfigurowanie zarządzania urządzeniami z systemem Windows z programu System Center Configuration Manager i Microsoft Intune."
ms.custom: na
ms.date: 03/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: "9"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 95808d4fd743d5cc18cacb69bb38bc729acdda25
ms.sourcegitcommit: 92c3f916e6bbd35b6208463ff406e0247664543a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2018
---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie hybrydowego zarządzania urządzeniami z systemem Windows za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat informuje administratorów IT, jak mogą oni dać użytkownikom dostosowania komputerów z systemem Windows i urządzeń przenośnych do zarządzania przy użyciu programu Configuration Manager i Microsoft Intune.

## <a name="enable-windows-device-management"></a>Włącz zarządzanie urządzeniami z systemem Windows
Aby włączyć zarządzanie urządzeniami z systemem Windows dla komputerów lub urządzeń przenośnych, należy użyć następujące czynności:

1.  Przed rozpoczęciem konfigurowania rejestracji dla dowolnej platformy spełnić wymagania wstępne i procedur w [Instalatora hybrydowego zarządzania urządzeniami Przenośnymi](setup-hybrid-mdm.md).  
2.  W konsoli programu Configuration Manager w **administracji** obszaru roboczego, przejdź do **omówienie** > **usługi w chmurze** > **subskrypcje usługi Microsoft Intune**.  
3.  Na wstążce kliknij **Konfiguruj platformy**, a następnie wybierz platformy systemu Windows:
    - **Windows** dla komputerów z systemem Windows i komputerów przenośnych, a następnie wykonaj następujące czynności:
      1. W **ogólne** , kliknij pozycję **Włącz rejestrację systemu Windows** wyboru.
      2. Jeśli używany certyfikat do podpisania kodu i wdróż aplikację Portal firmy, przejdź do **certyfikat podpisywania kodu**. Użytkownicy urządzeń można także zainstalować aplikację Portal firmy z Microsoft Store lub bez podpisywania kodu można wdrożyć aplikację z Microsoft Store dla firm.
      3. Można również skonfigurować [usługi Windows Hello dla firm ustawienia](windows-hello-for-business-settings.md).
    - **Windows Phone** dla systemu Windows, telefonów i tabletów, a następnie wykonaj następujące czynności:
      1. W **ogólne** , kliknij pozycję **Windows Phone 8.1 i Windows 10 Mobile** wyboru. Windows Phone 8.0 nie jest już obsługiwana.
      2. Jeśli Twoja organizacja musi ładować bezpośrednio aplikacji firmy, możesz przekazać wymagany token lub pliku. Aby uzyskać więcej informacji o aplikacjach pobierania lokalnego, zobacz [aplikacji Windows, Utwórz](https://docs.microsoft.com/sccm/apps/get-started/creating-windows-applications).
        - **Token rejestracji aplikacji**
        - **plik PFX**
        - **Brak** użycie certyfikatu firmy Symantec, można określić **Pokaż alert przed wygaśnie certyfikatach firmy Symantec**.
4. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  Aby uprościć proces rejestracji przy użyciu portalu firmy, należy utworzyć alias DNS do rejestracji urządzeń. Użytkownik może następnie poinformuj użytkowników, jak zarejestrować swoje urządzenia.

## <a name="choose-how-to-enroll-windows-devices"></a>Wybieranie metody rejestrowania urządzeń z systemem Windows

Po przypisaniu licencji usługi Intune dla użytkowników, bez żadnych dodatkowych kroków można rejestrować urządzeń z systemem Windows, ale użytkownik może ułatwić rejestracji dla użytkowników.

Dwa czynniki określają, jak można ułatwić rejestrację urządzenia systemu Windows:
- **Używasz usługi Azure Active Directory Premium?** <br>[Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) jest dołączana do pakietu Enterprise Mobility + Security i innych planów licencjonowania.
- **Które wersje klientów systemu Windows będą rejestrować?** <br>Urządzenia z systemem Windows 10 mogą rejestrować automatycznie przez dodanie konta firmowego lub szkolnego. Wcześniejszych wersji, należy zarejestrować za pomocą aplikacji Portal firmy.

||**Azure AD — wersja Premium**|**Inne usługi AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatycznego rejestrowania](#enable-windows-10-automatic-enrollment) |[Rejestrowanie użytkownika](#enable-windows-enrollment-without-azure-ad-premium)|
|**Starszych wersji systemu Windows**|[Rejestrowanie użytkownika](#enable-windows-enrollment-without-azure-ad-premium)|[Rejestrowanie użytkownika](#enable-windows-enrollment-without-azure-ad-premium)|

## <a name="enable-windows-10-automatic-enrollment"></a>Włączanie automatycznej rejestracji systemu Windows 10

Automatycznej rejestracji użytkownicy mogą rejestrować należące do firmy lub osobiste komputery z systemem Windows 10 i Windows 10 urządzeń przenośnych w usłudze Intune przez dodanie konta służbowego i uzgodnienia mają być zarządzane. Proste jak. W tle urządzenie użytkownika rejestruje i tworzy sprzężenie usługi Azure Active Directory. Po zarejestrowaniu, urządzenie jest zarządzane przez usługę Intune.

**Wymagania wstępne**
- Subskrypcję usługi Azure Active Directory Premium ([subskrypcji wersji próbnej](http://go.microsoft.com/fwlink/?LinkID=816845))
- Subskrypcja usługi Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurowanie automatycznej rejestracji MDM

1. Zaloguj się do [portalu zarządzania Azure](https://portal.azure.com) (https://manage.windowsazure.com) i wybierz **usługi Azure Active Directory**.

  ![Zrzut ekranu przedstawiający Azure portal](../media/auto-enroll-azure-main.png)

2. Wybierz **mobilności (Zarządzanie urządzeniami Przenośnymi i zarządzania aplikacjami Mobilnymi)**.

  ![Zrzut ekranu przedstawiający Azure portal](../media/auto-enroll-mdm.png)

3. Wybierz **usługi Microsoft Intune**.

  ![Zrzut ekranu przedstawiający Azure portal](../media/auto-enroll-intune.png)

4. Skonfiguruj **zakresie MDM użytkownika**. Określ urządzenia użytkowników, którzy mają być zarządzane przez program Microsoft Intune. Ci użytkownicy urządzeń z systemem Windows 10 zostanie automatycznie zarejestrowane na potrzeby zarządzania w usłudze Microsoft Intune.

    - **Brak**
    - **Niektóre**
    - **Wszystkie**

   ![Zrzut ekranu przedstawiający Azure portal](../media/auto-enroll-scope.png)

5. Użyj wartości domyślnych dla następujących adresów URL:
    - **Warunki zarządzania urządzeniami Przenośnymi, użyj adresu URL**
    - **Adres URL odnajdowania zarządzania urządzeniami Przenośnymi**
    - **Adres URL zgodności zarządzania urządzeniami Przenośnymi**

6. Wybierz **zapisać**.


Domyślnie uwierzytelnianie dwuskładnikowe nie jest włączone dla usługi. Jednak uwierzytelnianie dwuskładnikowe jest zalecane podczas rejestrowania urządzenia. Przed wymaganiem uwierzytelniania dwuskładnikowego dla tej usługi, należy skonfigurować dostawcę uwierzytelniania dwuskładnikowego w usłudze Azure Active Directory i skonfigurować konta użytkowników usługi Multi-Factor Authentication. Zobacz [wprowadzenie do korzystania z serwera usługi Azure Multi-Factor Authentication](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Włączanie rejestracji systemu Windows bez usługi Azure AD Premium
Można umożliwić użytkownikom rejestrowanie swoich urządzeń bez rejestracji automatycznej usługi Azure AD Premium. Po przypisaniu licencji, użytkownicy mogą rejestrować po dodaniu konta służbowego do swoich urządzeń osobistych lub łączenie ich urządzeń należących do usługi Azure AD. Utworzenie DNS alias (typ rekordu CNAME) ułatwia użytkownikom rejestrowanie swoich urządzeń. W przypadku utworzenia rekordu CNAME systemu DNS rekordów zasobów, użytkownikom łączenie się i rejestrowanie w usłudze Intune bez konieczności wprowadź nazwę serwera usługi Intune.

### <a name="create-cnames-to-simplify-enrollment"></a>Tworzenie rekordów CNAME w celu uproszczenia rejestracji
Utwórz CNAME DNS o rekordy zasobów dla domeny firmy. Na przykład jeśli witryna internetowa firmy to contoso.com, należy utworzyć rekord CNAME w systemie DNS, który przekierowuje domenę EnterpriseEnrollment.contoso.com do domeny enterpriseenrollment-s.manage.microsoft.com.

Mimo że tworzenie wpisów CNAME DNS jest opcjonalny, rekordy CNAME ułatwić rejestracji dla użytkowników. Jeśli zostanie znaleziony nie rejestracji rekord CNAME, monit ręcznie wprowadzić nazwę serwera zarządzania urządzeniami Przenośnymi enrollment.manage.microsoft.com.

|Typ|Nazwa hosta|Przekierowanie na|CZAS WYGAŚNIĘCIA|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.domena_firmy.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 godzina|

Jeśli masz więcej niż jeden sufiks nazwy UPN, należy utworzyć jeden CNAME dla każdej nazwy domeny, a następnie wskaż każdej z nich do domeny EnterpriseEnrollment-s.manage.microsoft.com. Na przykład, jeśli użytkownicy w firmie Contoso name@contoso.com, ale również użyć name@us.contoso.com, i name@eu.constoso.com jako wiadomości e-mail/nazw UPN, należy utworzyć śledzenie rekordów CNAME administrator DNS firmy Contoso.

|Typ|Nazwa hosta|Przekierowanie na|CZAS WYGAŚNIĘCIA|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 godzina|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 godzina|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 godzina|

`EnterpriseEnrollment-s.manage.microsoft.com`— Obsługuje przekierowanie do usługi Intune z rozpoznawaniem domeny na podstawie nazwy domeny adresu e-mail.

Zmiany rekordów DNS może potrwać do 72 godzin propagacji. Nie można zweryfikować zmiany w systemie DNS w usłudze Intune, dopóki trwa propagowanie rekordu DNS.

## <a name="tell-users-how-to-enroll-devices"></a>Poinformuj użytkowników, jak zarejestrować urządzenia  

 Po zakończeniu konfiguracji musisz poinformować użytkowników, jak mogą rejestrować swoje urządzenia. Zobacz [co mówić użytkownikom na temat rejestrowania ich urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) orientacji. Można przekierować użytkowników do [rejestrować urządzenia z systemem Windows w usłudze Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

> [!div class="button"]
[< Wstecz krok](create-service-connection-point.md)  [następny krok >  ](set-up-additional-management.md)
