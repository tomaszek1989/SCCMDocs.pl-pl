---
title: "Rejestrowanie urządzeń z systemem iOS z programu Device Enrollment Program (DEP) "
titleSuffix: Configuration Manager
description: "Włącz rejestracja Device Enrollment Program (DEP) dla hybrydowych wdrożeń w programie Configuration Manager przy użyciu usługi Intune dla systemu iOS."
ms.custom: na
ms.date: 09/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 78d44adc-9b1c-4bc6-b72d-e93873916ea6
caps.latest.revision: "9"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 1d8a1765b599daa98014feeb3d88efe9a07cb907
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="ios-device-enrollment-program-dep-enrollment-for-hybrid-deployments-with-configuration-manager"></a>Rejestracja systemu iOS Device Enrollment Program (DEP) dla hybrydowych wdrożeń z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Firmy mogą kupić urządzeń z systemem iOS za pośrednictwem programu device enrollment program firmy Apple i następnie zarządzać nimi za pomocą programu Microsoft Intune. W celu zarządzania firmowymi urządzeniami z systemem iOS przy użyciu programu Device Enrollment Program (DEP) firmy Apple należy wykonać czynności wymagane przez firmę Apple do uczestnictwa w programie i zakupić urządzenia w ramach tego programu. Szczegóły tego procesu są dostępne pod adresem:  [https://deploy.apple.com](https://deploy.apple.com). Zalety programu obejmują funkcję bezobsługowego konfigurowania urządzeń bez konieczności podłączania poszczególnych urządzeń do komputera przy użyciu połączenia USB.  

 Aby zarejestrować firmowe urządzenia z systemem iOS w programie DEP, należy uzyskać token programu DEP od firmy Apple. Token umożliwia usłudze Intune synchronizację informacji dotyczących urządzeń uczestniczących w programie DEP należących do firmy. Ponadto pozwala on usłudze Intune przekazywanie profilów rejestracji do firmy Apple i przypisywanie urządzeń do tych profilów.  

## <a name="apple-dep-enrollment-for-ios-devices"></a>Rejestracja urządzeń z systemem iOS w programie DEP firmy Apple  
 Poniższe procedury opisują sposób określania urządzeń z systemem iOS zakupionymi za pośrednictwem DEP firmy Apple jako zarządzanych przez usługę Intune urządzenia należące do firmy. Po pierwszym uprawnienia użytkownika Konfigurowanie urządzenia go będzie odbierać profil zarządzania DEP i uruchomić Asystenta ustawień i dostosować je do zarządzania.  

##  <a name="enable-dep-enrollment-in-configuration-manager-with-intune"></a>Włączanie rejestracji programu DEP w programie Configuration Manager z usługą Intune  

1.  **Rozpocznij zarządzanie urządzeniami z systemem iOS w programie Configuration Manager**   
    Aby można było zarejestrować urządzenia z systemem iOS Device Enrollment Program (DEP), należy wykonać kroki do [Konfigurowanie hybrydowego zarządzania urządzeniami przenośnymi](../../mdm/deploy-use/setup-hybrid-mdm.md) tym [kroki do obsługi rejestracji systemu iOS](../deploy-use/enroll-hybrid-ios-mac.md).
2.  **Utwórz żądanie tokenu DEP**   
    W konsoli programu Configuration Manager w **administracji** obszaru roboczego, rozwiń węzeł **Konfiguracja hierarchii**, rozwiń węzeł **usługi w chmurze**i kliknij przycisk **subskrypcje usługi Microsoft Intune**. Kliknij pozycję **Utwórz żądanie tokenu DEP** na karcie **Narzędzia główne** , kliknij pozycję **Przeglądaj** w celu wybrania lokalizacji pobierania dla żądania tokenu DEP, a następnie kliknij pozycję **Pobierz**. Zapisz lokalnie plik żądania tokenu DEP (pem). Plik pem jest używany na potrzeby żądania zaufanego tokenu (p7m) z portalu programu Device Enrollment Program firmy Apple.  
3.  **Pobierz token programu Device Enrollment Program**   
    Przejdź do [portalu programu Device Enrollment Program](https://deploy.apple.com) (https://deploy.apple.com) i zaloguj się przy użyciu identyfikatora Apple swojej firmy. Tego identyfikatora firmy Apple należy używać w przyszłości do odnawiania tokenu programu DEP.  
    1.  W konsoli programu [portalu programu Device Enrollment Program](https://deploy.apple.com)wybierz pozycję **Device Enrollment Program** > **Manage Servers**(Zarządzanie serwerami), a następnie kliknij pozycję **Add MDM Server**.  
    ![Zrzut ekranu przedstawiający Dodaj serwer MDM w portalu Device Enrollment Program](../media/enrollment-program-token-add-server.png)
    2.  Wprowadź nazwę serwera w polu **MDM Server Name**(Zarządzanie serwerami), a następnie kliknij pozycję **Next**. Nazwa serwera służy użytkownikowi do identyfikowania serwera MDM. Nie jest nazwa lub adres URL serwera usługi Intune lub programie Configuration Manager.  
    3.  **Add < nazwa_serwera\>**  zostanie otwarte okno dialogowe. Kliknij pozycję **Choose File… (Wybierz plik...)** w celu przesłania pliku pem utworzonego w poprzednim kroku, a następnie kliknij pozycję **Next**.  
    4.  **Add < nazwa_serwera\>**  Wyświetla okno dialogowe **Your Server Token** łącza. Pobierz plik tokenu serwera (p7m) na komputer, a następnie kliknij przycisk **Done**.  

     Ten plik certyfikatu (p7m) służy do ustanawiania relacji zaufania między serwerami usługi Intune i programu Device Enrollment Program firmy Apple.  
4.  **Dodaj token DEP do programu Configuration Manager**   
    W konsoli programu Configuration Manager w **administracji** obszaru roboczego, rozwiń węzeł **Konfiguracja hierarchii** i kliknij przycisk **subskrypcje usługi Microsoft Intune**. Kliknij pozycję **Konfiguruj platformy** na karcie **Narzędzia główne** i kliknij pozycję **iOS**. Wybierz pozycję **Włącz program Device Enrollment Program**, przejdź do pliku certyfikatu (p7m), a następnie kliknij kolejno pozycje **Otwórz**, **Przekaż**i **OK**.  

## <a name="add-a-corporate-device-enrollment-policy"></a>Dodaj zasady rejestracji urządzeń firmowych  

1. W konsoli programu Configuration Manager w **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **omówienie**, rozwiń węzeł **wszystkich firmowych urządzeń**, rozwiń węzeł **iOS**i kliknij przycisk **profile rejestracji**. Kliknij pozycję **Utwórz profil** na karcie **Narzędzia główne** , aby otworzyć Kreatora tworzenia profilu. Skonfiguruj ustawienia na następujących stronach:  
2. On the **Ogólne** określ poniższe informacje, a następnie kliknij przycisk **Next**.  
  -   **Nazwa** — nazwa profilu rejestracji urządzeń. (niewidoczne dla użytkowników)  
  -   **Opis elementu** — opis profilu rejestracji urządzeń. (niewidoczne dla użytkowników)  
  -   **Koligacja użytkownika** — określa sposób rejestracji urządzeń. Zobacz [koligacji użytkownika dla hybrydowych zarządzanych urządzeń w programie Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

      -  **Monituj o koligację użytkownika**: Urządzenia muszą być powiązane z użytkownikiem podczas początkowej konfiguracji, a następnie opcjonalnie zezwolić na dostęp do danych firmowych i poczty e-mail jako ten użytkownik.  Koligację użytkownika należy skonfigurować dla urządzeń zarządzanych w programie DEP, które należą do użytkowników i muszą korzystać z portalu firmy (tj. w celu instalowania aplikacji).  
      > [!NOTE]
      > DEP koligacji użytkownika wymaga punktu końcowego usług AD FS WS-Trust 1.3 nazwy użytkownika/Mixed włączenia do żądania tokenu użytkownika.

      -   **Brak koligacji użytkownika**: Urządzenie nie jest powiązany z użytkownikiem. Tego typu przynależności należy użyć w przypadku urządzeń wykonujących zadania bez uzyskiwania dostępu do danych użytkowników lokalnych. Aplikacje wymagające przynależności do użytkownika nie będą działać.  
    ![Zrzut ekranu DEP profilu nazwę, opis i wiersz koligacji użytkownika](../media/dep-general.png)

3. Na **ustawienia programu rejestracji urządzenia** , podaj następujące informacje, a następnie kliknij przycisk **dalej**.  
    -   **Dział**: Informacje te pojawiają się, gdy użytkownik naciśnie polecenie "Informacje o konfiguracji" podczas aktywacji.  
    -   **Numer telefonu pomocy technicznej**: Wyświetlane, gdy użytkownik kliknie **potrzebna pomoc** przycisk podczas aktywacji.
       ![Zrzut ekranu przedstawiający Przypisywanie profilu DEP do urządzeń z systemem iOS](../media/dep-settings.png)

    - **Tryb przygotowania**: Ten stan jest ustawiany podczas aktywacji i nie można zmienić bez zresetowania urządzenia fabryki:  
        -   **Nienadzorowane** — ograniczone możliwości zarządzania  
        -   **Nadzorowane** — włącza więcej opcji zarządzania i domyślnie wyłącza blokadę aktywacji  
    - **Zablokuj profil rejestracji dla urządzenia**: Ten stan jest ustawiany podczas aktywacji i nie można zmienić bez resetowania do ustawień fabrycznych.  
      -   **Wyłącz** — umożliwia profil zarządzania były usuwane z **ustawienia** menu  
      -   **Włącz** — (wymaga **tryb przygotowania** = **nadzorowane**) wyłącza ustawienia systemu iOS, które umożliwiają usunięcie profilu zarządzania  

4.  Na stronie **Asystent ustawień** skonfiguruj ustawienia umożliwiające dostosowanie asystenta ustawień systemu iOS uruchamianego po pierwszym włączeniu urządzenia, a następnie kliknij pozycję **Dalej**. Należą do nich następujące ustawienia:  
  -   **Kod dostępu** — wyświetla monit o podanie kodu dostępu podczas aktywacji. Zawsze wymagają hasła, chyba że urządzenia będą chronione lub mają dostęp steruje się w inny sposób (tj. tryb kiosku ograniczającej urządzenia do jednej aplikacji).  
  -   **Usługi lokalizacji** — Jeśli włączone, Asystent ustawień wyświetla monit dotyczący usługi podczas aktywacji  
  -   **Przywróć** — Jeśli włączone, Asystent ustawień wyświetla monit dla kopii zapasowej iCloud podczas aktywacji  
  -   **Identyfikator Apple ID** — identyfikator Apple ID jest wymagany do pobrania dla systemu iOS aplikacje w sklepie z aplikacjami, w tym zainstalowanych przez usługę Intune. Jeśli jest włączone, system iOS wyświetla monit podanie identyfikatora Apple ID podczas Intune będzie podejmowała próbę zainstalowania aplikacji bez identyfikatora.  
  -   **Warunki i postanowienia** — Jeśli włączone, Asystent ustawień monituje użytkowników o zaakceptowanie warunków i postanowień firmy Apple podczas aktywacji  
  -   **Touch ID** — Jeśli włączone, Asystent ustawień wyświetla monit dotyczący tej usługi podczas aktywacji
  -   **Apple Pay** — Jeśli włączone, Asystent ustawień wyświetla monit dotyczący tej usługi podczas aktywacji
  -   **Powiększenie** — Jeśli włączone, Asystent ustawień wyświetla monit dotyczący tej usługi podczas aktywacji
  -   **Używanie programu Siri** — Jeśli włączone, Asystent ustawień wyświetla monit dotyczący tej usługi podczas aktywacji  
  -   **Wyślij dane diagnostyczne do firmy Apple** — Jeśli włączone, Asystent ustawień wyświetla monit dotyczący tej usługi podczas aktywacji  
    ![Zrzut ekranu przedstawiający Przypisywanie profilu DEP do urządzeń z systemem iOS](../media/dep-setup-assistant.png)
5.  Na **na dodatkowe zarządzanie** Określ, czy ustawienia dodatkowego zarządzania można używać połączenia USB. Po wybraniu **wymagają certyfikatu**, należy zaimportować certyfikat zarządzania narzędzia Apple Configurator do użycia dla tego profilu.  Ustaw **nie Zezwalaj** aby zapobiec synchronizowaniu plików za pomocą programu iTunes lub zarządzaniu przy użyciu programu Apple Configurator. Firma Microsoft zaleca ustawienie **nie Zezwalaj**, wyeksportowanie dalszej konfiguracji z programu Apple Configurator, a następnie wdrożyć jako niestandardowego profilu konfiguracji systemu iOS, a nie Użyj tego ustawienia, aby umożliwić ręczne wdrożenie z lub bez certyfikatu.  

  -   **Nie zezwalaj na** — uniemożliwia urządzeniu komunikację za pośrednictwem połączenia USB (wyłącza parowanie)  
  -   **Zezwalaj na** — umożliwia urządzeniu komunikację za pośrednictwem połączenia USB z dowolnym komputerem PC lub Mac  
  -   **Wymagany certyfikat**— umożliwia parowanie z Mac przy użyciu certyfikatu zaimportowanego do profilu rejestracji  

## <a name="assign-dep-devices-for-management"></a>Przypisz urządzenia DEP do zarządzania

1. Przejdź do [portalu programu Device Enrollment Program](https://deploy.apple.com) (https://deploy.apple.com) i zaloguj się przy użyciu identyfikatora Apple swojej firmy.
2. Wybierz kolejno pozycje **Deployment Program** > **Device Enrollment Program** > **Manage Devices**. Określ sposób wyboru urządzeń w polu **Choose Devices**(Wybierz urządzenia), podaj informacje o urządzeniach i określ szczegóły według numeru seryjnego ( **Serial Number**) urządzenia lub numeru zamówienia ( **Order Number**) albo przekaż plik CSV ( **Upload CSV File**). Następnie wybierz pozycję **Przypisz serwerowi** i wybierz polecenie <*ServerName*> określoną w kroku 3, a następnie kliknij przycisk **OK**.  
![Zrzut ekranu z programem Device Enrollment Program portalu, dodawania urządzeń](../media/enrollment-program-token-specify-serial.png)

3.  **Zsynchronizuj urządzenia zarządzane w programie DEP**   
    W **zasoby i zgodność** obszaru roboczego, przejdź do **wszystkich firmowych urządzeń** > **wcześniej zadeklarowanej urządzeń**. Na karcie **Narzędzia główne** kliknij pozycję **Synchronizacja z programem DEP**. Żądanie synchronizacji zostanie wysłane do firmy Apple. Po zakończeniu synchronizacji zostaną wyświetlone urządzenia zarządzane w programie DEP.

    > [!NOTE]
    > W konfiguracji hybrydowego operacji synchronizacji z usługą DEP ręcznie jest wyzwalany przez kliknięcie przycisku **synchronizacji z usługą DEP** w konsoli programu Configuration Manager.

4.  **Przypisz profil DEP**<br>W **zasoby i zgodność** obszaru roboczego, przejdź do **wszystkich firmowych urządzeń** > **iOS** > **profile rejestracji**. Wybierz profil rejestracji DEP, a następnie w **Home** , kliknij pozycję **przypisany do urządzeń**. Wybierz urządzenia, które będą korzystać z tego profilu rejestracji, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **OK**.   
     ![Zrzut ekranu przedstawiający Przypisywanie profilu DEP do urządzeń z systemem iOS](../media/dep-assign-profile.png)

## <a name="distribute-devices-to-users"></a>Dystrybuuj urządzenia do użytkowników
Teraz możesz przekazać urządzenia firmowe użytkownikom. Zostanie otwarte okno dialogowe **Stan rejestracji** zarządzanych urządzeń to **Nie nawiązano komunikacji** , dopóki urządzenie nie zostanie włączone i Asystent ustawień nie zostanie uruchomiony w celu zarejestrowania urządzenia. Po włączeniu urządzenia z systemem iOS zostanie ono zarejestrowane na potrzeby zarządzania przez usługę Intune.
