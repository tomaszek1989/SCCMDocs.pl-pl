---
title: Wdróż aplikację Lookout pracy aplikacji
titleSuffix: Configuration Manager
description: Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych.
ms.date: 05/31/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 3f62b763-4347-453d-b0a7-1f4a0d1d4105
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 87ad7a768128cb11a1fc361c90a6eccac454a28c
ms.sourcegitcommit: 9cff0702c2cc0f214173b47ec241f7e5a40f84e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34752594"
---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule wyjaśniono, jak skonfigurować i wdrożyć aplikację Lookout for Work aplikacji dla urządzeń z systemami Android i iOS.



## <a name="android-google-play-store-app"></a>Android (w sklepie Google Play)
1.  W konsoli programu Configuration Manager kliknij **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

2.  Na stronie **Ogólne** Kreatora wdrażania oprogramowania podaj następujące informacje:  
    - Typ: Wybierz **pakiet aplikacji dla systemu Android w witrynie Google Play**.
    - Lokalizacja: kopiowanie aplikację Lookout for work link do aplikacji w sklepie Google Play jako wklej go w tym miejscu
    - Wydawca: Lookout zabezpieczeń urządzeń przenośnych
    - Nazwa: Lookout for Work
    - Opis: Lookout zapewnia najlepszą ochronę przed przenośnych zagrożeń dla bezpieczeństwa urządzenia. Po zainstalowaniu aplikacji Lookout aplikacji chroni urządzenia przed zagrożeniami. W przypadku odnalezienia żadnych zagrożeń, alerty możesz i administratora IT.
    - Kategoria administracyjna: Zarządzanie komputerem  

    Po pomyślnym zakończeniu zostanie wyświetlony na liście aplikacji Lookout for Work aplikacji.  

3.  Na **Home** karcie **wdrożenia** grupy, wybierz **Wdróż** Aby wdrożyć aplikację Lookout for Work aplikacji dla użytkowników.   
    >[!IMPORTANT]  
    >Musisz wybrać tej samej dodanych w opcji zarządzania rejestracji w konsoli Lookout MTP użytkowników.  

    Wybierz **wymagana instalacja** opcji. Ta opcja wymaga aplikacji Lookout do zainstalowania na urządzeniu użytkownika.  



## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (podpisane enterprise wersja aplikacji Lookout)

1. Upewnij się, że skonfigurowano Zarządzanie systemem iOS na urządzeniach. Aby uzyskać instrukcje dotyczące sposobu konfigurowania urządzenia do zarządzania systemem iOS, zobacz [Konfigurowanie iOS i Mac zarządzania urządzeniami](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).  

2. Ponowne podpisanie poszukaj pracy aplikacji dla systemu iOS. Lookout dystrybuuje jego szukać aplikacji dla systemu iOS pracy poza iOS App Store. Przed rozpoczęciem dystrybuowania aplikacji, należy ponownie podpisać aplikację z Enterprise Developer certyfikatów dla systemu iOS. Aby uzyskać szczegółowe instrukcje do ponownego podpisania poszukaj pracy aplikacji systemu iOS, zobacz [szukać proces ponownego podpisywania aplikacji systemu iOS pracy](https://personal.support.lookout.com/hc/articles/114094038714) w witrynie Lookout.  

3. Włącz uwierzytelnianie usługi Azure Active Directory (Azure AD) dla użytkowników systemu iOS.
   1.  Zaloguj się do [bloku usługi Azure AD z portalu Azure](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview), a następnie przejdź do strony rejestracji aplikacji.  
   2.  Określ nazwę jako **szukać aplikacji dla systemu iOS pracy**i wybierz **natywnego** jako typ aplikacji.  
  ![Zrzut ekranu okna dialogowego Dodaj aplikacje przedstawiający natywny klient opcji aplikacji](media/aad-add-app-reg.png)

   3.  Dla tego identyfikatora URI przekierowania, użyj następującego formatu: `lookoutwork://com.lookout.enterprise.<yourcompanyname>`, zastępując `<yourcompanyname>` nazwą swojej firmy. Na przykład: `lookoutwork://com.lookout.enterprise.contoso`
   4. Kliknij przycisk **Utwórz** do utworzenia aplikacji. 
   5.  Otwórz nową aplikację, kliknij pozycję **ustawienia**, i Dodaj dodatkowe identyfikator URI przekierowania. Użyj następującego formatu: `companyportal://code/<originalURI>`, gdzie `<originalURI>` jest wersją z oryginalnego identyfikatora URI przekierowania zakodowane w adresie URL. Na przykład `companyportal://code/lookoutwork%3A%2F%2Fcom.lookout.enterprise.contoso`
   6.  W ustawieniach aplikacji przejdź do **wymagane uprawnienia** i kliknij przycisk **Dodaj**. Wybierz następujące delegowane uprawnienia:  

       | INTERFEJS API  | Uprawnienia  |
       |---------|---------|
       | Lookout MTP     | Dostęp do Lookout MTP         |
       | Program Microsoft Graph     | Zaloguj się i odczytuj profil użytkownika        |  

   Aby uzyskać więcej informacji, zobacz [skonfigurować aplikację klienta natywnego](/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application).  


4. W programie Configuration Manager przekazać plik ponownie podpisany .ipa. Wartość minimalna wersja systemu operacyjnego do systemu iOS 8.0 lub nowszej. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji dla systemu iOS](/sccm/apps/get-started/creating-ios-applications).   


5. Tworzenie zasad konfiguracji aplikacji zarządzanej. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji mobilnej](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies).  


6. Wdróż aplikację Lookout for Work aplikacji dla użytkowników. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications).  

  Wybierz tym użytkownikom, które zostały dodane do opcji zarządzania rejestracji w konsoli Lookout. Wybierz **wymagana instalacja** opcji. Ta opcja wymaga aplikacji Lookout do zainstalowania na urządzeniu użytkownika.



## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Co się stanie po otwarciu aplikacji wdrożonych na urządzeniu

Gdy użytkownik otwiera aplikację Lookout for Work na urządzeniu, wyświetli je, aby aktywować aplikację. One powinien wybrać, zaloguj się przy użyciu opcji usługi Azure AD. Szczegółowy przewodnik z przepływem użytkownika końcowego znajduje się w następujących artykułach:

- [Zostanie wyświetlony monit o zainstalowanie aplikacji Lookout for Work na urządzeniu z systemem Android](/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)

- [Musisz rozwiązać zagrożenie znaleziono aplikację Lookout for Work na urządzeniu z systemem Android](/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)



## <a name="next-steps"></a>Następne kroki
- [Włącz regułę ochrony zagrożeń urządzenia w zasadach zgodności](enable-device-threat-protection-rule-compliance-policy.md)
