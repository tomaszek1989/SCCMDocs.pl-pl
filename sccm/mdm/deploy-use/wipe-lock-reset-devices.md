---
title: "Ochrona danych za pomocą czyszczenia danych, blokowania lub resetowania za pomocą programu System Center Configuration Manager kodu dostępu | Dokumentacja firmy Microsoft"
description: "Ochrona danych urządzenia za pomocą pełnego czyszczenia danych, selektywnego czyszczenia danych, zdalnego blokowania lub resetowania kodu dostępu przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 09/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: "18"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: ea92d7b4656a04f312f04c19cac6b17df931c9c5
ms.sourcegitcommit: db079cd7322e7d4926b2df0ccb37e752c570d902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/28/2017
---
# <a name="protect-data-with-remote-wipe-lock-or-passcode-reset-by-using-system-center-configuration-manager"></a>Ochrona danych za pomocą czyszczenia danych, blokowania lub resetowania za pomocą programu System Center Configuration Manager kodu dostępu

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager udostępnia selektywnego czyszczenia danych, pełnego czyszczenia danych, zdalnego blokowania i resetowania kodu dostępu. Urządzenia przenośne mogą zawierać poufne dane firmowe i umożliwiać dostęp do wielu zasobów firmowych. W celu ochrony urządzeń, możesz wykonywać:  

- Pełne czyszczenie danych w celu przywrócenia ustawień fabrycznych urządzenia.  

- Selektywne czyszczenie danych w celu usunięcia tylko danych firmowych.  

- Zdalna blokada w celu zabezpieczenia urządzenia, które mogło zostać utracone.  

- Resetowanie kodu dostępu urządzenia.  

## <a name="full-wipe"></a>Pełne czyszczenie danych  
Możesz wydać polecenie czyszczenia urządzenia, gdy zaistnieje potrzeba zabezpieczenia utraconego urządzenia lub wycofania urządzenia z aktywnego użycia.  

Wydaj polecenie **pełnego czyszczenia** urządzenia, aby przywrócić domyślne ustawienia fabryczne urządzenia. Spowoduje to usunięcie wszystkich danych firmowych oraz danych i ustawień użytkownika. Można wykonać pełne czyszczenie na urządzeniach Windows Phone, iOS, Android i Windows 10.  

> [!NOTE]
> Czyszczenie urządzeń z systemem Windows 10 w wersji wcześniejszej niż wersja 1511 z mniej niż 4 GB pamięci RAM może spowodować, że urządzenia będą odpowiadać. [Dowiedz się więcej](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram).

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Aby zainicjować zdalne czyszczenie danych z poziomu konsoli programu Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcje urządzeń** i wybrać odpowiednią kolekcję.  

2. Wybierz urządzenia, które chcesz wycofać/wyczyścić.  

3. Wybierz **akcje urządzeń zdalnych** w **grupy urządzeń**, a następnie wybierz pozycję **Wycofaj/wyczyść**.  

## <a name="selective-wipe"></a>Selektywne czyszczenie danych  
Aby usunąć tylko dane firmowe, wydaj polecenie **selektywnego czyszczenia** urządzenia. W poniższej tabeli opisano przez platformę, jakie dane zostaną usunięte i wpływa na dane, które pozostają zachowane w urządzeniu selektywne czyszczenie danych.  

**iOS**  

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|iOS|  
|--------------------------------------------|---------|  
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje zostaną odinstalowane. Dane aplikacji firmowych zostaną usunięte.|  
|Profile sieci VPN i Wi-Fi|Usuwane.|  
|Certyfikaty|Usuwane i odwołane.|  
|Ustawienia|Usunięte z wyjątkiem: **Zezwalaj na Roaming połączeń głosowych**, **Zezwalaj na roaming danych**, i **Zezwalaj na automatyczną synchronizację podczas roamingu**.|  
|Agent zarządzania|Profil zarządzania jest usuwany.|  
|Profile poczty e-mail|Konfigurowanie przez usługę Intune profilów poczty e-mail konto e-mail i wiadomości e-mail są usuwane.|  

**Android i Android Samsung KNOX Standard**  

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|Android|Samsung KNOX Standard|  
|--------------------------------------------|-------------|------------------|  
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje i dane pozostają zainstalowane.|Aplikacje zostaną odinstalowane.|  
|Profile sieci VPN i Wi-Fi|Usuwane.|Usuwane.|  
|Certyfikaty|Odwołano.|Odwołano.|  
|Ustawienia|Wymagania są usuwane.|Wymagania są usuwane.|  
|Agent zarządzania|Uprawnienie administratora urządzenia jest odwoływane.|Uprawnienie administratora urządzenia jest odwoływane.|  
|Profile poczty e-mail|Nie dotyczy.|Konfigurowanie przez usługę Intune profilów poczty e-mail konto e-mail i wiadomości e-mail są usuwane.|  

**Android for Work**

Podczas czyszczenia selektywnego w systemie Android pracy urządzenia usuwa profilu pracy oraz wszystkie dane, aplikacje i ustawienia w profilu pracy na tym urządzeniu. To wycofaniu urządzenia z zarządzania przy użyciu programu Configuration Manager i usługi Intune. Pełne czyszczenie danych nie jest obsługiwane dla systemu Android for Work.

 **Windows 10, Windows 8.1, Windows RT 8.1 i Windows RT**  

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|Windows 10, Windows 8.1 i Windows RT 8.1|  
|---------------------------------|-------------|
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje są dezinstalowane, a klucze ładowania bezpośredniego są usuwane. Aplikacje używające selektywne czyszczenie systemu Windows będzie mieć odwołanie klucza szyfrowania, a dane nie będą już dostępne.|  
|Profile sieci VPN i Wi-Fi|Usuwane.|  
|Certyfikaty|Usuwane i odwołane.|  
|Ustawienia|Wymagania są usuwane.|
|Agent zarządzania|Nie dotyczy. Agent zarządzania jest wbudowany.|  
|Profile poczty e-mail|Usunięte wiadomości e-mail z obsługą systemu szyfrowania plików, w tym aplikacji poczty dla systemu Windows w wiadomości e-mail i załączników.|  

 **Windows 10 Mobile, Windows Phone 8.0 i Windows Phone 8.1**

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|Windows 10 Mobile, Windows Phone 8 i Windows Phone 8.1|  
|-|-|
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje zostaną odinstalowane. Dane aplikacji firmowych zostaną usunięte.|  
|Profile sieci VPN i Wi-Fi|Usunąć dla systemu Windows 10 Mobile i Windows Phone 8.1.|  
|Certyfikaty|Usunięte w systemie Windows Phone 8.1.|  
|Agent zarządzania|Nie dotyczy. Agent zarządzania jest wbudowany.|  
|Profile poczty e-mail|Usunięte (z wyjątkiem Windows Phone 8.0).|  

Następujące ustawienia są także usuwane z urządzenia z systemem Windows 10 Mobile i Windows Phone 8.1:  

- **Wymagaj hasła do odblokowania urządzeń przenośnych**  
- **Zezwalaj na proste hasła**  
- **Minimalna długość hasła**  
- **Wymagany typ hasła**
- **Wygaśnięcie hasła (dni)**  
- **Pamiętaj historię haseł**  
- **Liczba dopuszczalnych nieudanych logowań przed usunięciem zawartości urządzenia**  
- **Liczba minut braku aktywności, zanim będzie wymagane hasło**  
- **Wymagany typ hasła — minimalna liczba zestawów znaków**  
- **Zezwalaj na używanie aparatu**
- **Wymagaj szyfrowania na urządzeniu przenośnym**  
- **Zezwalaj na używanie magazynu wymiennego**  
- **Zezwalaj na używanie przeglądarki sieci web**  
- **Zezwalaj na sklep z aplikacjami**  
- **Zezwalaj na przechwytywanie ekranu**  
- **Zezwalaj na używanie funkcji geolokalizacji**  
- **Zezwalaj na konto Microsoft**  
- **Zezwalaj na kopiowanie i wklejanie**  
- **Zezwalaj na tethering Wi-Fi**  
- **Zezwalaj na automatyczne łączenie z bezpłatnymi punktami HotSpot Wi-Fi**  
- **Zezwalaj na zgłaszanie hotspotów Wi-Fi**  
- **Zezwalaj na resetowanie do ustawień fabrycznych**
- **Zezwalaj na połączenia Bluetooth**  
- **Zezwalaj na komunikację NFC**
- **Zezwalaj na Wi-Fi**

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Aby zainicjować zdalne czyszczenie danych z poziomu konsoli programu Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcje urządzeń** i wybrać odpowiednią kolekcję.  

2. Wybierz urządzenia, które chcesz wycofać/wyczyścić.  

3. Wybierz **akcje urządzeń zdalnych** w **grupy urządzeń**, a następnie wybierz pozycję **Wycofaj/wyczyść**.  

## <a name="wiping-efs-enabled-content"></a>Czyszczenie zawartości z obsługą systemu szyfrowania plików  
Windows 8.1 i Windows RT 8.1 obsługuje selektywne czyszczenie zawartości z szyfrowania szyfrowania systemu plików. W przypadku selektywnego czyszczenia zawartości z obsługą systemu szyfrowania plików obowiązują następujące reguły:  

- Selektywne czyszczenie tylko aplikacji i danych chronionych przez system szyfrowania plików przy użyciu tej samej domeny internetowej co konto usługi Intune. Aby uzyskać więcej informacji, zobacz [Selektywne czyszczenie danych urządzenia w systemie Windows](http://technet.microsoft.com/library/dn486874.aspx).  

- Jeśli zmian w domenie skojarzonej z systemem szyfrowania plików, może zająć do 48 godzin przed aplikacje i dane, których używa nowej domeny można selektywnie wyczyścić.  

- Każda domena zarejestrowana w usłudze Intune jest domena, która zostanie wyczyszczona.  

Dane i aplikacje EFS selektywnego czyszczenia obecnie obsługuje są:  

- Aplikacja poczty dla systemu Windows.  

- Foldery robocze.

- Pliki i foldery zaszyfrowane w systemie szyfrowania plików. Aby uzyskać więcej informacji, zobacz [Najlepsze rozwiązania dotyczące systemu szyfrowania plików](http://support.microsoft.com/kb/223316).  

### <a name="best-practices-for-selective-wipe"></a>Najlepsze rozwiązania w zakresie selektywnego czyszczenia  

- Aby zapewnić powodzenie czyszczenia wiadomości e-mail należy skonfigurować profile poczty e-mail dla systemu iOS i Windows Phone 8.1 urządzeń.  

- Aby zapewnić powodzenie czyszczenia aplikacji upewnij się, że aplikacje są dystrybuowane za pomocą zarządzania aplikacjami dla urządzeń przenośnych.  

- Dla systemu iOS, należy skonfigurować ustawienie **Zezwalaj na tworzenie kopii zapasowych w ramach usługi iCloud** do **nie Zezwalaj** tak, aby użytkownicy nie mogli przywracać zawartości przy użyciu usługi iCloud.  

- Jeśli konto zostało dezaktywowane, następnie po roku Intune przestanie być konto i zostanie wykonane selektywne czyszczenie danych.  

##  <a name="passcode-reset"></a>Resetowanie kodu dostępu  
Jeśli użytkownik zapomni swój kod dostępu, możesz mu pomóc przez usunięcie kodu dostępu z urządzenia lub wymuszenie nowego hasła tymczasowego na urządzeniu. Poniższa tabela zawiera listę sposób resetowania kodu dostępu działa na różnych platformach mobilnych.  

|Platforma|Resetowanie kodu dostępu|  
|--------------|--------------------|  
|iOS|Obsługiwane czyszczenie kodu dostępu z urządzenia. Nie powoduje utworzenia nowego hasła tymczasowego.|
|System macOS| Nieobsługiwane.|
|Android|Obsługiwane i zostanie utworzony tymczasowy kod dostępu.|
|Android for Work | Nieobsługiwane.|
|Komputery z systemem Windows 10|Nieobsługiwane.|  
|Windows 10 mobile|Obsługiwane, z wyjątkiem usługi Azure AD przyłączone do urządzenia.|
|Windows Phone 8,1|Obsługiwane.|  
|Windows RT 8.1 |Nieobsługiwane.|  
|Komputery Windows 8.1 |Nieobsługiwane.|  

> [!Note]    
> Należy wykonać akcję resetowania kodu dostępu z lokacji najwyższego poziomu w danym środowisku. Na przykład jeśli korzystasz z centralną lokacją administracyjną akcję można wykonać tylko w tej witrynie. Jeśli używasz autonomiczną lokacją główną akcję można wykonać tylko w tej witrynie.

#### <a name="to-reset-the-passcode-on-a-mobile-device-remotely-in-configuration-manager"></a>Aby zdalnie zresetować kod dostępu na urządzeniu przenośnym w programie Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcje urządzeń** i wybrać odpowiednią kolekcję.  

2. Wybierz urządzenie lub urządzenia, na których chcesz zresetować kod dostępu.  

3. Wybierz **akcje urządzeń zdalnych** w **grupy urządzeń**, a następnie wybierz pozycję **Resetowanie kodu dostępu**.  

#### <a name="to-show-the-state-of-the-passcode-reset"></a>Aby wyświetlić stan resetowania kodu dostępu  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcje urządzeń** i wybrać odpowiednią kolekcję.  

2. Wybierz urządzenie lub urządzenia, na których chcesz wyświetlić stan resetowania kodu dostępu.  

3. Wybierz **akcje urządzeń zdalnych** w **grupy urządzeń**, a następnie wybierz pozycję **Pokaż stan kodu dostępu**.  

## <a name="remote-lock"></a>Zdalne blokowanie  
Jeśli użytkownik utraci urządzenie, można zdalnie zablokować urządzenie. W poniższej tabeli przedstawiono sposób zdalnego blokowania na różnych platformach mobilnych.  

|Platforma|Zdalne blokowanie|  
|--------------|-----------------|  
|iOS|Obsługiwane.|  
|Android|Obsługiwane.|  
|Windows 10|Obecnie nieobsługiwane.|  
|Windows Phone 8 i Windows Phone 8.1|Obsługiwane.|  
|Windows RT 8.1 |Obsługiwane, jeśli bieżący użytkownik urządzenia jest tym samym użytkownikiem, który zarejestrował urządzenie.|  
|Windows 8.1|Obsługiwane, jeśli bieżący użytkownik urządzenia jest tym samym użytkownikiem, który zarejestrował urządzenie.|  

> [!Note]    
> Należy wykonać akcję zdalne blokowanie z lokacji najwyższego poziomu w danym środowisku. Na przykład jeśli korzystasz z centralną lokacją administracyjną akcję można wykonać tylko w tej witrynie. Jeśli używasz autonomiczną lokacją główną akcję można wykonać tylko w tej witrynie.

#### <a name="to-lock-a-mobile-device-remotely-through-the-configuration-manager-console"></a>Aby zdalnie zablokować urządzenie przenośne za pośrednictwem konsoli programu Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcje urządzeń** i wybrać odpowiednią kolekcję.  

2. Wybierz urządzenie lub urządzenia do zablokowania.  

3. Wybierz **akcje urządzeń zdalnych** w **grupy urządzeń**, a następnie wybierz pozycję **zdalne blokowanie**.  

#### <a name="to-show-the-state-of-the-remote-lock"></a>Aby wyświetlić stan zdalnego blokowania  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcje urządzeń** i wybrać odpowiednią kolekcję.  

2. Wybierz urządzenie lub urządzenia, na których chcesz wyświetlić stan zdalnego blokowania.  

3. Wybierz **akcje urządzeń zdalnych** w **grupy urządzeń**, a następnie wybierz pozycję **Pokaż stan zdalnej blokady**.  

### <a name="see-also"></a>Zobacz także  
[Windows selektywne czyszczenie danych w celu zarządzania danymi urządzenia](http://technet.microsoft.com/library/dn486874.aspx)   
