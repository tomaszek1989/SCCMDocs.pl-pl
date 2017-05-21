---
title: "Konfigurowanie zarządzania urządzeniami hybrydowe systemu Windows za pomocą programu System Center Configuration Manager i Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Konfigurowanie zarządzania urządzeniami z systemem Windows za pomocą programu System Center Configuration Manager i Microsoft Intune."
ms.custom: na
ms.date: 03/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: dc1f70f5-64ab-42ab-aa91-d3858803e12f
caps.latest.revision: 9
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 329de5ffb6eb1403c02cd1db634c32f045e82488
ms.openlocfilehash: 47348baeac26bfa2ad5016622fe4dbcb9f572483
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-windows-hybrid-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfigurowanie hybrydowego zarządzania urządzeniami z systemem Windows za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera administratorów IT, jak pozwalają użytkownikom dostosowania komputery z systemem Windows i urządzeń przenośnych do zarządzania przy użyciu programu Configuration Manager i Microsoft Intune.

## <a name="enable-windows-device-management"></a>Włącz zarządzanie urządzeniami z systemem Windows
Aby włączyć zarządzanie urządzeniami systemu Windows dla komputerów PC i urządzeń przenośnych, wykonaj następujące kroki:

1.  Przed rozpoczęciem konfigurowania rejestracji dla dowolnej platformy ukończenia warunki wstępne i procedur w [Instalatora hybrydowe MDM](setup-hybrid-mdm.md).  
2.  W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, przejdź do **Przegląd** > **usług w chmurze** > **subskrypcje usługi Microsoft Intune**.  
3.  Na wstążce kliknij **Konfiguruj platformy**, a następnie wybierz platformę systemu Windows:
    - **Windows** na komputery z systemem Windows i przenośnych, a następnie wykonaj następujące czynności:
      1. W **ogólne** , kliknij pozycję **rejestracji Windows włączyć** pole wyboru.
      2. Jeśli używany certyfikat do podpisania kodu i wdrażania aplikacji Portal firmy, przejdź do **certyfikat podpisywania kodu**. Użytkownicy urządzeń można także zainstalować aplikacji Portal firmy ze Sklepu Windows lub bez podpisywania kodu można wdrożyć aplikację w Sklepie Windows dla firm.
      3. Można również skonfigurować [Windows Hello ustawień Business](windows-hello-for-business-settings.md).
    - **Windows Phone** dla systemu Windows telefony i tablety, a następnie wykonaj następujące czynności:
      1. W **ogólne** , kliknij pozycję **Windows Phone 8.1 i Windows 10 Mobile** pole wyboru. Windows Phone 8.0 nie jest już obsługiwana.
      2. Jeśli Twoja organizacja musi ładować bezpośrednio aplikacji firmy, można przekazać pliku lub wymagany token. Aby uzyskać więcej informacji o aplikacjach pobierania lokalnego, zobacz [aplikacji dla systemu Windows tworzenie](https://docs.microsoft.com/sccm/apps/get-started/creating-windows-applications).
        - **Token rejestracji aplikacji**
        - **plik PFX**
        - **Brak** użycie certyfikatu firmy Symantec, można określić **Pokaż alert, zanim wygaśnie certyfikatach firmy Symantec**.
4. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  Aby uprościć proces rejestracji przy użyciu portalu firmy, należy utworzyć alias DNS do rejestracji urządzeń. Użytkownik może następnie poinformuj użytkowników, jak zarejestrować swoje urządzenia.

## <a name="choose-how-to-enroll-windows-devices"></a>Wybierz sposób rejestrowania urządzeń z systemem Windows

Po przypisaniu licencji usługi Intune dla użytkowników, urządzeń z systemem Windows można zarejestrować bez żadnych dodatkowych kroków, ale użytkownik może ułatwić rejestracji dla użytkowników.

Jak można uprościć rejestrowania urządzenia z systemem Windows decydują dwa czynniki:
- **Używasz Azure Active Directory Premium?** <br>[Usługi Azure AD Premium](https://docs.microsoft.com/azure/active-directory/active-directory-get-started-premium) dołączona Enterprise Mobility + zabezpieczeń i innych programów licencjonowania.
- **Które wersje klientów z systemem Windows będą rejestrować?** <br>Urządzenia z systemem Windows 10 mogą rejestrować automatycznie przez dodanie konta służbowego. Wcześniejszych wersji, należy zarejestrować przy użyciu aplikacji Portal firmy.

||**Usługi Azure AD Premium**|**Inne usługi AD**|
|----------|---------------|---------------|  
|**Windows 10**|[Automatyczne rejestrowanie](#enable-windows-10-automatic-enrollment) |[Rejestracja użytkownika](#enable-windows-enrollment-without-azure-ad-premium)|
|**Starszych wersji systemu Windows**|[Rejestracja użytkownika](#enable-windows-enrollment-without-azure-ad-premium)|[Rejestracja użytkownika](#enable-windows-enrollment-without-azure-ad-premium)|

## <a name="enable-windows-10-automatic-enrollment"></a>Włącz automatyczne rejestrowanie systemu Windows 10

Automatyczne rejestrowanie pozwala użytkownikom rejestrować należące do firmy lub osobiste komputery z systemem Windows 10 i Windows 10 urządzenia przenośne w usłudze Intune przez dodanie konta służbowego i akceptując mają być zarządzane. Prosta jako. W tle urządzenie użytkownika rejestruje i tworzy sprzężenie Azure Active Directory. Po zarejestrowaniu, urządzenie jest zarządzane przy użyciu usługi Intune.

**Wymagania wstępne**
- Subskrypcja platformy Azure Active Directory Premium ([subskrypcji wersji próbnej](http://go.microsoft.com/fwlink/?LinkID=816845))
- Subskrypcja usługi Microsoft Intune


### <a name="configure-automatic-mdm-enrollment"></a>Konfigurowanie automatycznej rejestracji MDM

1. Zaloguj się do [portalu zarządzania Azure](https://portal.azure.com) (https://manage.windowsazure.com) i wybierz **Azure Active Directory**.

  ![Zrzut ekranu przedstawiający portalu Azure](../media/auto-enroll-azure-main.png)

2. Wybierz **mobilności (MDM i MAM)**.

  ![Zrzut ekranu przedstawiający portalu Azure](../media/auto-enroll-mdm.png)

3. Wybierz **usługi Microsoft Intune**.

  ![Zrzut ekranu przedstawiający portalu Azure](../media/auto-enroll-intune.png)

4. Skonfiguruj **zakresie MDM użytkownika**. Określ użytkowników, których urządzenia powinny być zarządzane przez program Microsoft Intune. Urządzenia systemu Windows 10 Ci użytkownicy zostaną automatycznie zarejestrowane zarządzania w usłudze Microsoft Intune.

    - **Brak**
    - **Niektóre**
    - **Wszystkie**

   ![Zrzut ekranu przedstawiający portalu Azure](../media/auto-enroll-scope.png)

5. Użyj wartości domyślnych dla następujących adresów URL:
    - **MDM Użyj adres URL warunków użytkowania**
    - **Adres URL odnajdowania MDM**
    - **Adres URL zgodności MDM**

6. Wybierz **zapisać**.


Domyślnie uwierzytelniania dwuetapowego nie jest włączone dla usługi. Jednak uwierzytelniania dwuetapowego zaleca się podczas rejestrowania urządzenia. Wymagają uwierzytelniania dwuetapowego dla tej usługi, należy skonfigurować dostawcę uwierzytelniania dwuetapowego w usłudze Active Directory Azure i skonfigurować konta użytkownika dla uwierzytelniania wieloskładnikowego. Zobacz [wprowadzenie do korzystania z serwera uwierzytelniania wieloskładnikowego Azure](https://docs.microsoft.com/azure/multi-factor-authentication/multi-factor-authentication-get-started-cloud).

## <a name="enable-windows-enrollment-without-azure-ad-premium"></a>Włącz rejestrowanie dla systemu Windows bez Azure AD Premium
Można umożliwić użytkownikom rejestrowanie swoich urządzeń bez automatycznego rejestrowania Azure AD Premium. Po przypisaniu licencji, użytkownicy mogą rejestrować po dodaniu konta pracy ze swoimi urządzeniami osobistymi lub łączenie ich urządzeń należących do usługi Azure AD. Tworzenie DNS alias (typ rekordu CNAME) ułatwia użytkownikom rejestrowanie swoich urządzeń. W przypadku utworzenia rekordu CNAME systemu DNS rekordy zasobów użytkowników połączenia i zarejestrować w usłudze Intune bez konieczności wprowadź nazwę serwera usługi Intune.

### <a name="create-cnames-to-simplify-enrollment"></a>Utwórz rekordy CNAME w celu uproszczenia rejestracji
Utwórz rekordy zasobów dla domeny firmy CNAME w systemie DNS. Na przykład jeśli witryna internetowa firmy to contoso.com, należy utworzyć rekord CNAME w systemie DNS, który przekierowuje domenę EnterpriseEnrollment.contoso.com do enterpriseenrollment-s.manage.microsoft.com.

Tworzenie wpisów CNAME DNS jest opcjonalne, rekordy CNAME łatwiejsze rejestracji dla użytkowników. Jeśli zostanie wykryte nie rejestracji rekord CNAME, użytkownicy są monitowani o ręcznie wprowadzić nazwę serwera MDM enrollment.manage.microsoft.com.

|Typ|Nazwa hosta|Przekierowanie na|CZAS WYGAŚNIĘCIA|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.domena_firmy.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 godzina|

Jeśli masz więcej niż jeden sufiks głównej nazwy użytkownika, należy utworzyć jeden CNAME dla każdej nazwy domeny i wskaż każdą z nich EnterpriseEnrollment-s.manage.microsoft.com. Na przykład, jeśli użytkownicy w Contoso używać name@contoso.com, ale także użyć name@us.contoso.com, i name@eu.constoso.com jako adres e-mail/nazw UPN, należy utworzyć następujące rekordy CNAME administrator Contoso DNS.

|Typ|Nazwa hosta|Przekierowanie na|CZAS WYGAŚNIĘCIA|  
|----------|---------------|---------------|---|
|CNAME|EnterpriseEnrollment.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 godzina|
|CNAME|EnterpriseEnrollment.us.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com|1 godzina|
|CNAME|EnterpriseEnrollment.eu.contoso.com|EnterpriseEnrollment-s.manage.microsoft.com| 1 godzina|

`EnterpriseEnrollment-s.manage.microsoft.com`— Obsługuje przekierowanie do usługi Intune z rozpoznawaniem domeny na podstawie nazwy domeny adresu e-mail.

Zmiany rekordów DNS może potrwać do 72 godzin propagowanie. Nie można zweryfikować zmiany DNS w usłudze Intune, dopóki propaguje rekordu DNS.

## <a name="tell-users-how-to-enroll-devices"></a>Poinformuj użytkowników, jak zarejestrować urządzenia  

 Po zakończeniu konfiguracji musisz poinformować użytkowników, jak mogą rejestrować swoje urządzenia. Zobacz [co mówić użytkownikom dotyczące rejestrowania urządzeń](https://docs.microsoft.com/intune/deploy-use/what-to-tell-your-end-users-about-using-microsoft-intune) orientacji. Przekierować użytkowników do [zarejestrować urządzenie z systemem Windows w usłudze Intune](https://docs.microsoft.com/intune/enduser/enroll-your-device-in-intune-windows). Te informacje dotyczą urządzeń przenośnych zarządzanych zarówno przez usługę Microsoft Intune, jak i program Configuration Manager.

> [!div class="button"]
[< Wstecz kroku](create-service-connection-point.md)[następny krok >  ](set-up-additional-management.md)

