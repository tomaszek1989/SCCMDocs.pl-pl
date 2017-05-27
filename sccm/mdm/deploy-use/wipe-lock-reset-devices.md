---
title: "Ochrona danych za pomocą czyszczenia danych, blokowania lub resetowania za pomocą programu System Center Configuration Manager kodu dostępu | Dokumentacja firmy Microsoft"
description: "Ochrona danych urządzenia za pomocą pełnego czyszczenia danych, selektywne czyszczenie, zdalne blokowanie lub resetowania kodu dostępu przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 770da7bd-02dd-474a-9604-93ff1ea0c1e4
caps.latest.revision: 18
caps.handback.revision: 0
author: nathbarn
ms.author: nathbarn
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dda2f4c01078fbbd174cbcb30357554c24f6abeb
ms.openlocfilehash: 351fdc6328dd0859d60e00b128963df738e69f81
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="protect-data-with-remote-wipe-lock-or-passcode-reset-by-using-system-center-configuration-manager"></a>Ochrona danych za pomocą czyszczenia danych, blokowania lub resetowania za pomocą programu System Center Configuration Manager kodu dostępu

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager zapewnia selektywne czyszczenie danych, pełnego czyszczenia danych, zdalnego blokowania i resetowania kodu dostępu możliwości. Urządzenia przenośne mogą zawierać poufne dane firmowe i umożliwiać dostęp do wielu zasobów firmowych. W celu ochrony urządzeń, można wydać:  

- Pełne czyszczenie danych w celu przywrócenia ustawień fabrycznych urządzenia.  

- Selektywne czyszczenie danych w celu usunięcia tylko danych firmowych.  

- Zdalna blokada w celu zabezpieczenia urządzenia, które mogło zostać utracone.  

- Resetowanie kodu dostępu urządzenia.  

## <a name="full-wipe"></a>Pełne czyszczenie danych  
Możesz wydać polecenie czyszczenia urządzenia, gdy zaistnieje potrzeba zabezpieczenia utraconego urządzenia lub wycofania urządzenia z aktywnego użycia.  

Wydaj polecenie **pełnego czyszczenia** urządzenia, aby przywrócić domyślne ustawienia fabryczne urządzenia. Spowoduje to usunięcie wszystkich danych firmowych oraz danych i ustawień użytkownika. Można wykonać pełne czyszczenie danych na urządzeniach Windows Phone, iOS, Android i Windows 10.  

> [!NOTE]
> Czyszczenie urządzeń z systemem Windows 10 w wersjach starszych niż wersja 1511 mniej niż 4 GB pamięci RAM mogą pozostać, urządzenie nie odpowiada. [Dowiedz się więcej](https://technet.microsoft.com/library/mt592024.aspx#full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram).

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Aby zainicjować zdalne czyszczenie danych z poziomu konsoli programu Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcji urządzeń** i wybierz kolekcję.  

2. Wybierz urządzenia, które chcesz wycofać/wyczyścić.  

3. Wybierz **zdalnego akcji urządzenia** w **grupy urządzeń**, a następnie wybierz **wycofywania i czyszczenia**.  

## <a name="selective-wipe"></a>Selektywne czyszczenie danych  
Aby usunąć tylko dane firmowe, wydaj polecenie **selektywnego czyszczenia** urządzenia. W poniższej tabeli opisano platformy, jakie dane zostaną usunięte i wpływu na dane, które pozostają na urządzeniu po selektywnego czyszczenia.  

**iOS**  

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|iOS|  
|--------------------------------------------|---------|  
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje zostaną odinstalowane. Dane aplikacji firmowych zostaną usunięte.|  
|Profile sieci VPN i Wi-Fi|Usuwane.|  
|Certyfikaty|Usuwane i odwołane.|  
|Ustawienia|Usunięte z wyjątkiem: **Zezwalaj na Roaming połączeń głosowych**, **Zezwalaj na roaming danych**, i **Zezwalaj na automatyczną synchronizację podczas roamingu**.|  
|Agent zarządzania|Profil zarządzania jest usuwany.|  
|Profile poczty e-mail|Profili poczty e-mail przez usługę Intune konto e-mail i wiadomości e-mail zostaną usunięte.|  

**Android i Android Samsung KNOX Standard**  

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|Android|KNOX Samsung Standard|  
|--------------------------------------------|-------------|------------------|  
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje i dane pozostają zainstalowane.|Aplikacje zostaną odinstalowane.|  
|Profile sieci VPN i Wi-Fi|Usuwane.|Usuwane.|  
|Certyfikaty|Odwołano.|Odwołano.|  
|Ustawienia|Wymagania są usuwane.|Wymagania są usuwane.|  
|Agent zarządzania|Uprawnienie administratora urządzenia jest odwoływane.|Uprawnienie administratora urządzenia jest odwoływane.|  
|Profile poczty e-mail|Nie dotyczy.|Profili poczty e-mail przez usługę Intune konto e-mail i wiadomości e-mail zostaną usunięte.|  

**Android do pracy**

Sposób selektywnego czyszczenia danych w systemie Android pracy urządzenia Usuwa profil pracy oraz wszystkie dane, aplikacje i ustawienia w profilu pracy z tego urządzenia. Urządzenie to wycofaniu z zarządzania za pomocą programu Configuration Manager i usługi Intune. Pełne czyszczenie danych nie jest obsługiwana dla systemu Android do pracy.

 **Windows 10, Windows 8.1, Windows RT 8.1 i Windows RT**  

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|Windows 10, Windows 8.1 i Windows RT 8.1|  
|---------------------------------|-------------|
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje są dezinstalowane, a klucze ładowania bezpośredniego są usuwane. Aplikacje, które używają selektywne czyszczenie systemu Windows będzie miał odwołanie klucza szyfrowania, a dane przestają być dostępne.|  
|Profile sieci VPN i Wi-Fi|Usuwane.|  
|Certyfikaty|Usuwane i odwołane.|  
|Ustawienia|Wymagania są usuwane.|
|Agent zarządzania|Nie dotyczy. Agent zarządzania jest wbudowany.|  
|Profile poczty e-mail|Usunięte wiadomości e-mail z obsługą systemu szyfrowania plików, w tym z aplikacji poczty dla systemu Windows w wiadomości e-mail i załączniki.|  

 **Windows 10 Mobile, Windows Phone 8.0 i Windows Phone 8.1**

|Zawartość usuwana podczas w przypadku wycofywania urządzenia|Windows 10 Mobile, Windows Phone 8 i Windows Phone 8.1|  
|-|-|
|Aplikacje firmowe i skojarzone dane zainstalowane za pomocą programu Configuration Manager i usługi Intune|Aplikacje zostaną odinstalowane. Dane aplikacji firmowych zostaną usunięte.|  
|Profile sieci VPN i Wi-Fi|Usunięte w systemie Windows 10 Mobile i Windows Phone 8.1.|  
|Certyfikaty|Usunięte w systemie Windows Phone 8.1.|  
|Agent zarządzania|Nie dotyczy. Agent zarządzania jest wbudowany.|  
|Profile poczty e-mail|Usunięte (z wyjątkiem Windows Phone 8.0).|  

Następujące ustawienia są także usuwane z urządzenia Windows 10 Mobile i Windows Phone 8.1:  

- **Wymagaj hasła do odblokowania urządzeń przenośnych**  
- **Zezwalaj na proste hasła**  
- **Minimalna długość hasła**  
- **Wymagany typ hasła**
- **Wygaśnięcie hasła (dni)**  
- **Pamiętaj historię haseł**  
- **Liczba dopuszczalnych nieudanych logowań przed wyczyszczeniem danych z urządzenia**  
- **Liczba minut braku aktywności, zanim będzie wymagane hasło**  
- **Wymagany typ hasła — minimalna liczba zestawów znaków**  
- **Zezwalaj na używanie aparatu**
- **Wymagaj szyfrowania na urządzeniu przenośnym**  
- **Zezwalaj na używanie magazynu wymiennego**  
- **Zezwalaj na używanie przeglądarki sieci web**  
- **Zezwalaj na sklep aplikacji**  
- **Zezwalaj na przechwytywanie ekranu**  
- **Zezwalaj na używanie funkcji geolokalizacji**  
- **Zezwalaj na konto Microsoft**  
- **Zezwalaj na kopiowanie i wklejanie**  
- **Zezwalaj na tethering Wi-Fi**  
- **Zezwalaj na automatyczne łączenie z bezpłatnymi punktami HotSpot Wi-Fi**  
- **Zezwalaj na raportowanie informacji o hotspotach Wi-Fi**  
- **Zezwalaj na resetowanie do ustawień fabrycznych**
- **Zezwalaj na połączenia Bluetooth**  
- **Zezwalaj na komunikację NFC**
- **Zezwalaj na Wi-Fi**

#### <a name="to-initiate-a-remote-wipe-from-the-configuration-manager-console"></a>Aby zainicjować zdalne czyszczenie danych z poziomu konsoli programu Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcji urządzeń** i wybierz kolekcję.  

2. Wybierz urządzenia, które chcesz wycofać/wyczyścić.  

3. Wybierz **zdalnego akcji urządzenia** w **grupy urządzeń**, a następnie wybierz **wycofywania i czyszczenia**.  

## <a name="wiping-efs-enabled-content"></a>Czyszczenie zawartości z obsługą systemu szyfrowania plików  
Windows 8.1 i Windows RT 8.1 obsługuje selektywnego czyszczenia zawartości szyfrowane szyfrowania systemu plików. W przypadku selektywnego czyszczenia zawartości z obsługą systemu szyfrowania plików obowiązują następujące reguły:  

- Selektywnie są tylko aplikacje i dane, które są chronione przez system szyfrowania plików za pomocą tej samej domeny internetowej co konto usługi Intune. Aby uzyskać więcej informacji, zobacz [Selektywne czyszczenie danych urządzenia w systemie Windows](http://technet.microsoft.com/library/dn486874.aspx).  

- Jeśli zmiany zostaną wprowadzone w domenie skojarzonej z systemem szyfrowania plików, może zająć do 48 godzin przed aplikacje i dane, których używa nowej domeny można selektywnie.  

- Każda domena zarejestrowana w usłudze Intune jest domena, która zostanie wyczyszczona.  

Dane i aplikacje EFS selektywnego czyszczenia aktualnie obsługuje są:  

- Aplikacja poczty dla systemu Windows.  

- Foldery robocze.

- Pliki i foldery zaszyfrowane w systemie szyfrowania plików. Aby uzyskać więcej informacji, zobacz [Najlepsze rozwiązania dotyczące systemu szyfrowania plików](http://support.microsoft.com/kb/223316).  

### <a name="best-practices-for-selective-wipe"></a>Najlepsze rozwiązania w zakresie selektywnego czyszczenia danych  

- Aby zapewnić powodzenie czyszczenia wiadomości e-mail należy skonfigurować profile poczty e-mail do urządzeń Windows Phone 8.1 i iOS.  

- Aby zapewnić powodzenie czyszczenia aplikacje upewnij się, że aplikacje są rozpowszechniane za pośrednictwem funkcji zarządzania aplikacjami dla urządzeń przenośnych.  

- W przypadku systemu iOS skonfiguruj ustawienie **Zezwalaj na tworzenie kopii zapasowych w ramach usługi iCloud** do **nie Zezwalaj** tak, aby użytkownicy nie mogli przywracać zawartości przy użyciu usługi iCloud.  

- Jeśli konto zostało dezaktywowane, następnie po roku Intune przestanie być konto i zostanie wykonane selektywne czyszczenie danych.  

##  <a name="passcode-reset"></a>Resetowanie kodu dostępu  
Jeśli użytkownik zapomni swój kod dostępu, możesz mu pomóc przez usunięcie kodu dostępu z urządzenia lub wymuszenie nowego hasła tymczasowego na urządzeniu. Poniższa tabela zawiera listę sposób działania na różnych platformach mobilnych resetowania kodu dostępu.  

|Platforma|Resetowanie kodu dostępu|  
|--------------|--------------------|  
|iOS|Obsługiwane czyszczenie kodu dostępu z urządzenia. Nie powoduje utworzenia nowego hasła tymczasowego.|
|macOS| Nieobsługiwane.|
|Android|Obsługiwane, i utworzeniu hasła tymczasowego.|
|Android for Work | Nieobsługiwane.|
|Komputery z systemem Windows 10|Nieobsługiwane.|  
|System Windows 10 przenośnych|Obsługiwane, z wyłączeniem Azure AD przyłączona do urządzenia.|
|Windows Phone 8,1|Obsługiwane.|  
|Windows RT 8.1 |Nieobsługiwane.|  
|Komputery Windows 8.1 |Nieobsługiwane.|  

#### <a name="to-reset-the-passcode-on-a-mobile-device-remotely-in-configuration-manager"></a>Aby zdalnie zresetować kod dostępu na urządzeniu przenośnym w programie Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcji urządzeń** i wybierz kolekcję.  

2. Wybierz urządzenie lub urządzenia, na których chcesz zresetować kod dostępu.  

3. Wybierz **zdalnego akcji urządzenia** w **grupy urządzeń**, a następnie wybierz **Resetowanie kodu dostępu**.  

#### <a name="to-show-the-state-of-the-passcode-reset"></a>Aby wyświetlić stan resetowania kodu dostępu  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcji urządzeń** i wybierz kolekcję.  

2. Wybierz urządzenie lub urządzenia, na których chcesz wyświetlić stan resetowania kodu dostępu.  

3. Wybierz **zdalnego akcji urządzenia** w **grupy urządzeń**, a następnie wybierz **Pokaż kod dostępu stanu**.  

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

#### <a name="to-lock-a-mobile-device-remotely-through-the-configuration-manager-console"></a>Aby zdalnie zablokować urządzenie przenośne za pośrednictwem konsoli programu Configuration Manager  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcji urządzeń** i wybierz kolekcję.  

2. Wybierz urządzenie lub urządzenia do zablokowania.  

3. Wybierz **zdalnego akcji urządzenia** w **grupy urządzeń**, a następnie wybierz **zdalne blokowanie**.  

#### <a name="to-show-the-state-of-the-remote-lock"></a>Aby wyświetlić stan zdalnego blokowania  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność** i wybierz polecenie **urządzeń**. Alternatywnie można wybrać **kolekcji urządzeń** i wybierz kolekcję.  

2. Wybierz urządzenie lub urządzenia, na których chcesz wyświetlić stan zdalnego blokowania.  

3. Wybierz **akcji urządzenia zdalnego** w **grupy urządzeń**, a następnie wybierz **Pokaż stan blokady zdalnego**.  

### <a name="see-also"></a>Zobacz także  
[Windows selektywne czyszczenie danych w celu zarządzania danymi urządzenia](http://technet.microsoft.com/library/dn486874.aspx)   

