---
title: Wdróż aplikację Lookout pracy aplikacji
titleSuffix: Configuration Manager
description: Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3f62b763-4347-453d-b0a7-1f4a0d1d4105
caps.latest.revision: ''
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 01c388377948ab362d60951cb8398a9276e668fb
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym artykule wyjaśniono, jak skonfigurować i wdrożyć aplikację Lookout for Work aplikacji dla urządzeń z systemami Android i iOS.

## <a name="android-google-play-store-app"></a>Android (aplikacji ze sklepu Google Play)
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

- **Krok 1.** Upewnij się, że **zarządzania w systemie iOS** jest skonfigurowany na urządzeniu. Aby uzyskać instrukcje dotyczące sposobu konfigurowania urządzenia do zarządzania systemem iOS, zobacz [Konfigurowanie iOS i Mac zarządzania urządzeniami](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac).

- **Krok 2.** **Ponowne podpisanie** poszukaj pracy aplikacji dla systemu iOS. Lookout dystrybuuje jego szukać aplikacji dla systemu iOS pracy poza iOS App Store. **Przed rozpoczęciem dystrybuowania aplikacji**, należy ponownie podpisać aplikację z Enterprise Developer certyfikatów dla systemu iOS. Aby uzyskać szczegółowe instrukcje do ponownego podpisania poszukaj pracy aplikacji systemu iOS, zobacz [szukać proces ponownego podpisywania aplikacji systemu iOS pracy](https://personal.support.lookout.com/hc/articles/114094038714) w witrynie Lookout.


- **Krok 3.** Włącz uwierzytelnianie usługi Azure Active Directory dla użytkowników systemu iOS, wykonując następujące czynności:
  1.  Zaloguj się do [portalu zarządzania usługi Azure Active Directory](https:/portal.azure.com), a następnie przejdź do strony aplikacji.
  2.  Dodaj **szukać aplikacji dla systemu iOS pracy** jako **aplikację native client**.
  ![Zrzut ekranu okna dialogowego Dodaj aplikacje przedstawiający natywny klient opcji aplikacji](media/aad-add-app.png)

  3. Zastąp **com.lookout.enterprise.yourcompanyname** z klientem pakietu identyfikator wybranego po podpisaniu IPA.
  4.  Dodaj identyfikator URI przekierowania dodatkowe:  **&lt;companyportal://code/ >** następuje URLencoded wersji oryginalnej identyfikator URI przekierowania.
  5.  Dodaj **delegowane uprawnienia** do aplikacji.

  Aby uzyskać więcej informacji, zobacz [skonfigurować aplikację klienta natywnego](/azure/app-service/app-service-mobile-how-to-configure-active-directory-authentication#optional-configure-a-native-client-application).


- **Krok 4.** Przekaż plik IPA ponownie podpisany, zgodnie z opisem w [tworzenie aplikacji systemu iOS w programie System Center Configuration Manager temacie](/sccm/apps/get-started/creating-ios-applications) tematu. Wartość minimalna wersja systemu operacyjnego do systemu iOS 8.0 lub nowszej.


- **Krok 5.** Tworzenie zasad konfiguracji aplikacji zarządzanej, zgodnie z opisem w [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji mobilnych w programie System Center Configuration Manager](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies) tematu.


- **Krok 6.** **Umożliwia wdrażanie aplikacji dla użytkowników**, wybierz aplikację Lookout for Work aplikacji w **aplikacji** strony, od **Home** karcie **wdrożenia** grupy, wybierz  **Wdrażanie**.

  Wybierz tym użytkownikom, które zostały dodane do opcji zarządzania rejestracji w konsoli Lookout. Wybierz **wymagana instalacja** opcji. Ta opcja wymaga aplikacji Lookout do zainstalowania na urządzeniu użytkownika.



## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Co się stanie po otwarciu aplikacji wdrożonych na urządzeniu

Gdy użytkownik otwiera aplikację Lookout for Work na urządzeniu, wyświetli je, aby aktywować aplikację. One powinien wybrać, zaloguj się przy użyciu opcji Azure Active Directory. Szczegółowy przewodnik z przepływem użytkownika końcowego znajduje się w następujących artykułach:

- [Zostanie wyświetlony monit o zainstalowanie aplikacji Lookout for Work na urządzeniu z systemem Android](/intune-user-help/you-are-prompted-to-install-lookout-for-work-android)

- [Musisz rozwiązać zagrożenie znaleziono aplikację Lookout for Work na urządzeniu z systemem Android](/intune-user-help/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)



## <a name="next-steps"></a>Następne kroki
- [Włącz regułę ochrony zagrożeń urządzenia w zasadach zgodności](enable-device-threat-protection-rule-compliance-policy.md)
