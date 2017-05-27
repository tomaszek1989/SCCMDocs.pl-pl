---
title: "Rejestrowanie urządzeń z systemem iOS z Device Enrollment Program (DEP) - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Włącz iOS Device Enrollment Program (DEP) rejestracji dla wdrożenia hybrydowego w programie Configuration Manager za pomocą usługi Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: 9
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 5b5eadd7b4026eae59acceaef43cdacd7a33d3ac
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>rejestrowanie dla systemu iOS Device Enrollment Program (DEP) dla wdrożenia hybrydowego z programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Firmy można kupić urządzeń z systemem iOS za pośrednictwem programu device enrollment program firmy Apple i zarządzać nimi za pomocą programu Microsoft Intune. W celu zarządzania firmowymi urządzeniami z systemem iOS przy użyciu programu Device Enrollment Program (DEP) firmy Apple należy wykonać czynności wymagane przez firmę Apple do uczestnictwa w programie i zakupić urządzenia w ramach tego programu. Szczegóły tego procesu są dostępne pod adresem:  [https://deploy.apple.com](https://deploy.apple.com). Zalety programu obejmują funkcję bezobsługowego konfigurowania urządzeń bez konieczności podłączania poszczególnych urządzeń do komputera przy użyciu połączenia USB.  

 Aby zarejestrować firmowe urządzenia z systemem iOS w programie DEP, należy uzyskać token programu DEP od firmy Apple. Token umożliwia usłudze Intune synchronizację informacji dotyczących urządzeń uczestniczących w programie DEP należących do firmy. Umożliwia również usłudze Intune przekazywanie profilów rejestracji do firmy Apple i przypisywanie urządzeń do tych profilów.  

## <a name="apple-dep-enrollment-for-ios-devices"></a>Rejestracja urządzeń z systemem iOS w programie DEP firmy Apple  
 Poniższe procedury opisują sposób określenia urządzeń z systemem iOS kupionymi za pośrednictwem DEP firmy Apple, jako zarządzane Intune urządzenia należące do firmy. Gdy konto użytkownika uprawnień pierwsze urządzenie go będzie odbierać profil zarządzania DEP i uruchomić Asystenta ustawień i dostosowania ich do zarządzania.  

###  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>Włączanie DEP rejestracji w programie Configuration Manager za pomocą usługi Intune  

1.  **Rozpocznij zarządzanie urządzeniami z systemem iOS w programie Configuration Manager**   
    Przed zarejestrowaniem urządzenia z systemem iOS Device Enrollment Program (DEP), należy wykonać kroki, aby [skonfigurować zarządzanie urządzeniami przenośnymi hybrydowe](../../mdm/deploy-use/setup-hybrid-mdm.md) tym [kroki, aby obsługiwać rejestrację iOS](../deploy-use/enroll-hybrid-ios-mac.md).

2.  **Utwórz żądanie tokenu DEP**   
    W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, rozwiń węzeł **Konfiguracja hierarchii**, rozwiń węzeł **usług w chmurze**i kliknij przycisk **subskrypcje usługi Microsoft Intune**. Kliknij pozycję **Utwórz żądanie tokenu DEP** na karcie **Narzędzia główne** , kliknij pozycję **Przeglądaj** w celu wybrania lokalizacji pobierania dla żądania tokenu DEP, a następnie kliknij pozycję **Pobierz**. Zapisz lokalnie plik żądania tokenu DEP (pem). Plik pem jest używany na potrzeby żądania zaufanego tokenu (p7m) z portalu programu Device Enrollment Program firmy Apple.  

3.  **Pobierz token programu Device Enrollment Program**   
    Przejdź do [portalu programu Device Enrollment Program](https://deploy.apple.com) (https://deploy.apple.com) i zaloguj się przy użyciu identyfikatora Apple swojej firmy. Tego identyfikatora firmy Apple należy używać w przyszłości do odnawiania tokenu programu DEP.  

    1.  W konsoli programu [portalu programu Device Enrollment Program](https://deploy.apple.com)wybierz pozycję **Device Enrollment Program** > **Manage Servers**(Zarządzanie serwerami), a następnie kliknij pozycję **Add MDM Server**.  

    2.  Wprowadź nazwę serwera w polu **MDM Server Name**(Zarządzanie serwerami), a następnie kliknij pozycję **Next**. Nazwa serwera służy użytkownikowi do identyfikowania serwera MDM. Nie jest nazwa lub adres URL serwera usługi Intune lub programu Configuration Manager.  

    3.  **Add < ServerName\>**  zostanie otwarte okno dialogowe. Kliknij pozycję **Choose File… (Wybierz plik...)** w celu przesłania pliku pem utworzonego w poprzednim kroku, a następnie kliknij pozycję **Next**.  

    4.  **Add < ServerName\>**  Wyświetla okno dialogowe **Your Server tokenu** łącza. Pobierz plik tokenu serwera (p7m) na komputer, a następnie kliknij przycisk **Done**.  

     Ten plik certyfikatu (p7m) służy do ustanawiania relacji zaufania między serwerami usługi Intune i programu Device Enrollment Program firmy Apple.  

4.  **Dodaj token DEP do programu Configuration Manager**   
    W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, rozwiń węzeł **Konfiguracja hierarchii** i kliknij przycisk **subskrypcje usługi Microsoft Intune**. Kliknij pozycję **Konfiguruj platformy** na karcie **Narzędzia główne** i kliknij pozycję **iOS**. Wybierz pozycję **Włącz program Device Enrollment Program**, przejdź do pliku certyfikatu (p7m), a następnie kliknij kolejno pozycje **Otwórz**, **Przekaż**i **OK**.  

#### <a name="set-up-enrollment-for-apple-device-enrollment-program-dep-ios-devices"></a>Konfigurowanie rejestracji urządzeń z systemem iOS Program rejestracji urządzeń firmy Apple (DEP)  

1.  **Dodaj zasady rejestracji urządzeń firmowych**   
    W konsoli programu Configuration Manager w **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **Przegląd**, rozwiń węzeł **wszystkich urządzeń należących do**, rozwiń węzeł **iOS**i kliknij przycisk **profile rejestracji**. Kliknij pozycję **Utwórz profil** na karcie **Narzędzia główne** , aby otworzyć Kreatora tworzenia profilu. Skonfiguruj ustawienia na następujących stronach:  

    1.  On the **Ogólne** określ poniższe informacje, a następnie kliknij przycisk **Next**.  

        -   **Nazwa** — nazwa profilu rejestracji urządzeń. (niewidoczne dla użytkowników)  

        -   **Opis** — opis profilu rejestracji urządzeń. (niewidoczne dla użytkowników)  

        -   **Koligacja użytkownika** — określa sposób rejestracji urządzeń. Zobacz [koligacji użytkownika dla hybrydowego zarządzanych urządzeń w programie Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

            -   **Monituj o koligację użytkownika**: Urządzenia muszą być powiązane z użytkownika podczas instalacji początkowej oraz można zezwolić na dostęp do danych firmowych i poczty e-mail jako ten użytkownik.  Koligację użytkownika należy skonfigurować dla urządzeń zarządzanych w programie DEP, które należą do użytkowników i muszą korzystać z portalu firmy (tj. w celu instalowania aplikacji).  

            > [!NOTE]
            > DEP dzięki koligacji użytkownika wymaga punktu końcowego usług AD FS WS-Trust 1.3 nazwy użytkownika/mieszane, aby mieć możliwość żądania tokenu użytkownika.

            -   **Brak koligacji użytkownika**: Urządzenie nie jest powiązany z użytkownikiem. Tego typu przynależności należy użyć w przypadku urządzeń wykonujących zadania bez uzyskiwania dostępu do danych użytkowników lokalnych. Aplikacje wymagające przynależności do użytkownika nie będą działać.  
             ![Zrzut ekranu DEP profilu nazwę, opis i wiersz koligację użytkownika](../media/dep-general.png)

    2.  Na **ustawień programu rejestracji urządzeń** , podaj następujące informacje, a następnie kliknij przycisk **dalej**.  

        -   **Dział**: Te informacje są wyświetlane, gdy użytkownicy naciśnij przycisk "Dotyczące konfiguracji" podczas aktywacji.  

        -   **Numer pomocy technicznej**: Wyświetlane, gdy użytkownik kliknie przycisk **uzyskać Pomoc** przycisk podczas aktywacji.
       ![Zrzut ekranu przedstawiający Przypisywanie profilu DEP do urządzeń z systemem iOS](../media/dep-settings.png)

        -   **Tryb przygotowania**: Ten stan jest ustawiony podczas aktywacji i nie można zmienić bez fabryki zresetowanie urządzenia:  

            -   **Bez kontroli** -ograniczone możliwości zarządzania  

            -   **Nadzorowane** — umożliwia więcej opcji zarządzania i domyślnie wyłącza blokadę aktywacji  

        -   **Zablokuj profil rejestracji dla urządzenia**: Ten stan jest ustawiony podczas aktywacji i nie można zmienić bez resetowane do ustawień fabrycznych.  

            -   **Wyłącz** -umożliwia profil zarządzania, który ma zostać usunięty z **ustawienia** menu  

            -   **Włącz** -(wymaga **trybie przygotowania** = **Supervised**) wyłącza ustawień systemu iOS, które mogłyby umożliwić usunięcie profilu zarządzania  

    3.  Na stronie **Asystent ustawień** skonfiguruj ustawienia umożliwiające dostosowanie asystenta ustawień systemu iOS uruchamianego po pierwszym włączeniu urządzenia, a następnie kliknij pozycję **Dalej**. Należą do nich następujące ustawienia:  
        -   **Kod dostępu** — monitu dla kodu dostępu podczas aktywacji. Zawsze wymagają kodu dostępu, chyba że urządzenie będzie zabezpieczony lub mają dostęp kontrolowany w inny sposób (tj. tryb kiosku ograniczający urządzenia do jednej aplikacji).  
        -   **Usługi lokalizacji** — Jeśli włączono Asystenta monity usługi podczas aktywacji  
        -   **Przywróć** — Jeśli włączono Asystenta monituje o iCloud kopii zapasowej podczas aktywacji  
        -   **Identyfikator firmy Apple** — identyfikator firmy Apple są wymagane do pobierania iOS App Store aplikacji, łącznie z tymi zainstalowane przez usługę Intune. Włączenie iOS będzie monitował użytkowników dla Identyfikatora firmy Apple, gdy Intune spróbuje zainstalować aplikację bez identyfikatora.  
        -   **Warunki i postanowienia** -włączenie Asystenta monituje użytkowników, aby zaakceptować warunki i postanowienia firmy Apple podczas aktywacji  
        -   **Touch ID** — Jeśli włączono Asystenta monity dla tej usługi podczas aktywacji
        -   **Zapłać Apple** — Jeśli włączono Asystenta monity dla tej usługi podczas aktywacji
        -   **Powiększenie** — Jeśli włączono Asystenta monity dla tej usługi podczas aktywacji
        -   **Siri** — Jeśli włączono Asystenta monity dla tej usługi podczas aktywacji  
        -   **Wyślij dane diagnostyczne do firmy Apple** — Jeśli włączono Asystenta monity dla tej usługi podczas aktywacji  
        ![Zrzut ekranu przedstawiający Przypisywanie profilu DEP do urządzeń z systemem iOS](../media/dep-setup-assistant.png)

    4.  Na **dodatkowego zarządzania** Określ, czy połączenie USB mogą być używane dla ustawienia dodatkowego zarządzania. Po wybraniu **wymagają certyfikatu**, należy zaimportować certyfikat zarządzania programu Apple Configurator dla tego profilu.  Ustaw **nie Zezwalaj** aby zapobiec synchronizowanie plików za pomocą programu iTunes lub zarządzania przy użyciu programu Apple Configurator. Firma Microsoft zaleca, możesz ustawić **nie Zezwalaj**, eksportowanie dalszej konfiguracji z programu Apple Configurator i następnie wdrożyć jako niestandardowy profil konfiguracji systemu iOS, zamiast Użyj tego ustawienia, aby zezwolić na ręczne wdrożenie z użyciem lub bez certyfikatu.  

        -   **Nie zezwalaj na** -urządzenia zapobiega komunikacji przy użyciu kabla USB (wyłącza parowania)  

        -   **Zezwalaj na** -umożliwia urządzenia komunikują się za pośrednictwem połączenia USB za pomocą dowolnego komputera PC lub Mac  

        -   **Wymaga certyfikatu**— umożliwia kojarzenie z Mac za pomocą certyfikatu importowane do profilu rejestracji  

2.  **Przypisz urządzenia DEP do zarządzania**   
    Przejdź do [portalu programu Device Enrollment Program](https://deploy.apple.com) (https://deploy.apple.com) i zaloguj się przy użyciu identyfikatora Apple swojej firmy. Wybierz kolejno pozycje **Deployment Program** > **Device Enrollment Program** > **Manage Devices**. Określ sposób wyboru urządzeń w polu **Choose Devices**(Wybierz urządzenia), podaj informacje o urządzeniach i określ szczegóły według numeru seryjnego ( **Serial Number**) urządzenia lub numeru zamówienia ( **Order Number**) albo przekaż plik CSV ( **Upload CSV File**). Następnie wybierz pozycję **Przypisz do serwera** i wybierz polecenie <*ServerName*> określonego w kroku 3, a następnie kliknij przycisk **OK**.  

3.  **Zsynchronizuj urządzenia zarządzane w programie DEP**   
    W **zasoby i zgodność** obszaru roboczego, przejdź do **wszystkich urządzeń należących do** > **Predeclared urządzeń**. Na karcie **Narzędzia główne** kliknij pozycję **Synchronizacja z programem DEP**. Żądanie synchronizacji zostanie wysłane do firmy Apple. Po zakończeniu synchronizacji zostaną wyświetlone urządzenia zarządzane w programie DEP.

4.  **Przypisz profil DEP**<br>W **zasoby i zgodność** obszaru roboczego, przejdź do **wszystkich urządzeń należących do** > **iOS** > **profile rejestracji**. Wybierz profil rejestracji DEP i następnie w **Home** , kliknij pozycję **przypisany do urządzeń**. Wybierz urządzenia, które będą korzystały z tego profilu rejestracji, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **OK**.   
     ![Zrzut ekranu przedstawiający Przypisywanie profilu DEP do urządzeń z systemem iOS](../media/dep-assign-profile.png)

5.  **Dystrybuuj urządzenia do użytkowników**   
    Teraz możesz przekazać urządzenia firmowe użytkownikom. Zostanie otwarte okno dialogowe **Stan rejestracji** zarządzanych urządzeń to **Nie nawiązano komunikacji** , dopóki urządzenie nie zostanie włączone i Asystent ustawień nie zostanie uruchomiony w celu zarejestrowania urządzenia. Po włączeniu urządzenia z systemem iOS zostanie ono zarejestrowane na potrzeby zarządzania przez usługę Intune.

