---
title: "Wdrażanie ewentualnym pracy aplikacji | Dokumentacja firmy Microsoft"
description: "Konfigurowanie i wdrażanie ewentualnym dla aplikacji do pracy."
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
caps.latest.revision: 
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 59f43c922d1d3bc64625733014b0def1e42c4d2d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-and-deploy-lookout-for-work-apps"></a>Konfigurowanie i wdrażanie ewentualnym pracy aplikacji

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym artykule opisano sposób konfigurowania i wdrażania szukać pracy aplikacji dla urządzeń z systemami Android i iOS.

## <a name="android-google-play-store-app"></a>Android (aplikacja do sklepu Google Play)
1.  W konsoli programu Configuration Manager kliknij **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.

2.  Na stronie **Ogólne** Kreatora wdrażania oprogramowania podaj następujące informacje:
  * Typ: Wybierz **pakiet aplikacji dla systemu Android w witrynie Google Play**.
  * Lokalizacja: kopiowanie szukać łącze aplikacji do pracy ze sklepu Google Play jako wklej go tutaj
  * Wydawcy: Ewentualnym zabezpieczeń urządzeń przenośnych
  * Nazwa: Szukać pracy
  * Opis: Ewentualnym zapewnia najlepsze ochronę przed zagrożeniami przenośnych w celu zabezpieczenia urządzenia. Po zainstalowaniu aplikacji ewentualnym na urządzeniu chroni przed zagrożeniami urządzenia i wyświetli alert można, a administrator firmy po znalezieniu aplikacji.
  * Kategoria administracyjna: Zarządzanie komputerem

  Po pomyślnym zakończeniu zostanie wyświetlona szukać pracy aplikacji na liście aplikacji.

3.  Na **Home** w karcie **wdrożenia** grupy, wybierz **Wdróż** wdrażanie szukać aplikacji pracy użytkowników.
>[!IMPORTANT]
>Należy wybrać tych samych użytkowników dodane w opcji zarządzania rejestracji w konsoli ewentualnym MTP.

  Wybierz **wymagana instalacja** możliwość wymagają zainstalowania aplikacji ewentualnym na urządzeniu użytkownika.

## <a name="ios-enterprise-signed-version-of-lookout-app"></a>iOS (podpisane Enterprise wersja aplikacji ewentualnym)

* **Krok 1:** Upewnij się, **zarządzania iOS** skonfigurowano na urządzeniu. Aby uzyskać instrukcje na temat sposobu instalacji urządzenia do zarządzania systemem iOS, zobacz [Konfigurowanie iOS i Mac zarządzanie urządzeniami]().

* **Krok 2:** **Ponowne podpisanie** szukać aplikacji iOS pracy. Ewentualnym dystrybuuje jego szukać aplikacji iOS pracy poza iOS App Store. **Przed rozpoczęciem dystrybuowania aplikacji**, aplikacja musi ponownie podpisać z Twojej iOS certyfikat dewelopera Enterprise. Szczegółowe instrukcje będzie ponowne podpisanie szukać pracy aplikacji, zobacz [szukać ponownie proces podpisywania aplikacji iOS pracy](https://personal.support.lookout.com/hc/en-us/articles/114094038714) w witrynie szczególną.


* **Krok 3:** Włącz uwierzytelnianie Azure Active Directory dla użytkowników systemu iOS, wykonując następujące czynności:
  1.  Logowanie do [portalu zarządzania Azure Active Directory](https://manage.windowsazure.com)i przejdź do strony aplikacji.
  2.  Dodaj **szukać aplikacji iOS pracy** jako **klientami aplikacji**.
  ![Zrzut ekranu okna dialogowego Dodaj aplikacje przedstawiający macierzystego klienta opcję aplikacji](media/aad-add-app.png)

  3. Zastąp **com.lookout.enterprise.yourcompanyname** z klientem wybrano podczas tworzenia IPA identyfikator pakietu.
  4.  Dodaj dodatkowe przekierowania identyfikatora URI:  **&lt;companyportal://code/ >** następuje wersji URLencoded swoje oryginalne przekierowania URI.
  5.  Dodaj **delegować uprawnienia** do swojej aplikacji.

  Aby uzyskać więcej informacji, zobacz [skonfigurować aplikację klienta macierzystego](https://azure.microsoft.com/en-us/documentation/articles/app-service-mobile-how-to-configure-active-directory-authentication/#optional-configure-a-native-client-application).


* **Krok 4:** Przekaż plik .ipa ponownie podpisany, zgodnie z opisem w [tworzenie aplikacji systemu iOS w temacie programu System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/apps/get-started/creating-ios-applications) tematu. Ustaw minimalną wersję systemu operacyjnego iOS 8.0 lub nowszy.


* **Krok 5.** Tworzenie zasad konfiguracji zarządzaną aplikację, zgodnie z opisem w [skonfigurowanie aplikacji systemu iOS z aplikacji mobilnej zasady konfiguracji w programie System Center Configuration Manager](https://docs.microsoft.com/en-us/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies) tematu.


* **Krok 6:** **Wdrażania aplikacji dla użytkowników**, wybierz szukać pracy aplikacji w **aplikacje** strona, z **Home** karcie w **wdrożenia** grupy, wybierz **Wdróż**.

  Należy wybrać tych samych użytkowników, które zostały dodane do opcji zarządzania rejestracji w konsoli szczególną.  
Wybierz **wymagana instalacja** możliwość wymagają zainstalowania aplikacji ewentualnym na urządzeniu użytkownika.

## <a name="what-happens-when-the-deployed-app-is-opened-on-the-device"></a>Co się stanie po otwarciu aplikacji wdrożonych na urządzeniu




Kiedy użytkownik otwiera szukać pracy na urządzeniu są monitowani o uaktywnić aplikację, a następnie wybierz Zaloguj się przy użyciu opcji Azure Active Directory. Szczegółowy przewodnik z przepływem przez użytkownika końcowego można znaleźć w następujących tematach:

* [Zostanie wyświetlony monit o zainstalowanie szukać pracy na urządzeniu z systemem Android](http://docs.microsoft.com/intune/enduser/you-are-prompted-to-install-lookout-for-work-android)

* [Należy rozwiązać zagrożeniem szukać pracy znalezione na urządzeniu z systemem Android](http://docs.microsoft.com/intune/enduser/you-need-to-resolve-a-threat-found-by-lookout-for-work-android)

## <a name="next-steps"></a>Następne kroki
* [Włącz zasadę ochrony zagrożenia urządzenia w zasadach zgodności](enable-device-threat-protection-rule-compliance-policy.md)

