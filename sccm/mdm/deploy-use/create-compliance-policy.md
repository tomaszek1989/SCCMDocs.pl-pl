---
title: "Tworzenie i wdrażanie zasad zgodności urządzeń | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak utworzyć i wdrożyć zasady zgodności urządzeń w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0fd76043-d7ee-423d-8c5f-aa7e9ed58ce0
caps.latest.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
robots: noindex
ms.translationtype: Machine Translation
ms.sourcegitcommit: 216d288aa7b7f2b98df86f59355d879366dcd44d
ms.openlocfilehash: 4baa6e0fe009f5f7dc33f5ab4adb1ec5e5c5271b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="create-and-deploy-a-device-compliance-policy"></a>Tworzenie i wdrażanie zasad zgodności urządzeń

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


## <a name="create-a-compliance-policy"></a>Tworzenie zasad zgodności

1.  W konsoli programu System Center Configuration Manager wybierz **zasoby i zgodność**.

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz **zasady zgodności**.

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz zasady zgodności**.

4.  Na **ogólne** strona kreatora tworzenia zasad zgodności Podaj następujące informacje:

  * **Nazwa**. Wprowadź unikatową nazwę zasady zgodności. Można użyć maksymalnie 256 znaków.

  * **Opis**. Wprowadź opis, który umożliwia identyfikowanie profilu sieci VPN i pomaga zidentyfikować go w konsoli programu Configuration Manager. Można użyć maksymalnie 256 znaków.

  * **Zasady zgodności typu**. Wybierz typ zasad, który chcesz utworzyć, w zależności od tego, czy urządzenie jest zarządzane przez program Configuration Manager. Odnosi się do wersji lub nowszej.<br /><br /> W przypadku urządzeń zarządzanych przez usługę Intune wybierz opcję **Reguły zgodności dla urządzeń zarządzanych bez klienta programu Configuration Manager** . Po wybraniu tej opcji należy również wybierz typ platformy, która ma te zasady, które dotyczą.

  * **Waga niezgodności raportów**. Określ poziom ważności zgłaszany w przypadku oceny tych zasad zgodności jako niezgodnych. Dostępne są następujące poziomy ważności:

     * **Brak**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.
     * **Informacje o**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.   
     * **Ostrzeżenie**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.
     * **Krytyczne**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.
     * **Krytyczne ze zdarzeniem**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.      

5.  Na **obsługiwane platformy** wybierz platformy urządzeń, które zostanie obliczone w tych zasad zgodności, lub wybierz **Zaznacz wszystko** aby wybrać wszystkie platformy urządzeń. Obsługiwane platformy to: Windows 7, Windows 8.1 i Windows 10; Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 i Windows Server 2016.

6.  Na stronie **Reguły** należy zdefiniować co najmniej jedną regułę definiującą konfigurację urządzenia, która umożliwia ocenienie urządzenia jako zgodnego. Po utworzeniu zasady zgodności niektóre reguły są domyślnie włączone, ale można je edytować lub usunąć. Pełna lista wszystkich zasad Zobacz sekcję "Reguły zasad zgodności" w dalszej części tego tematu.

  > [!NOTE]  
  >  Na komputery z systemem Windows Windows 8.1 w wersji systemu operacyjnego jest raportowana jako 6.3 zamiast 8.1. Jeśli zasada wersji systemu operacyjnego jest ustawiony na Windows 8.1 dla systemu Windows, następnie urządzenia będą raportowane jako niezgodne, nawet jeśli urządzenie Windows 8.1. Upewnij się, to ustawienie po prawej stronie *zgłosił* wersji systemu Windows dla reguł systemu operacyjnego minimalne i maksymalne. Numer wersji musi być zgodna z wersją który **winver** polecenie zwraca. Ten problem nie występuje w przypadku telefonów z systemem Windows. Wersja jest zgłaszana zgodnie z oczekiwaniami jako wersja 8.1. Komputery z systemem Windows w systemie operacyjnym Windows 10, aby uzyskać wersję należy ustawić jako **10.0** plus numerze kompilacji systemu operacyjnego **winver** polecenie zwraca.

7.  Na **Podsumowanie** strony kreatora przejrzyj wprowadzone ustawienia, a następnie Zakończ pracę kreatora.

 Nowe zasady pojawia się w **zasady zgodności** węzła **zasoby i zgodność** obszaru roboczego.

## <a name="deploy-a-compliance-policy"></a>Wdrażanie zasad zgodności

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz **zasady zgodności**.

3.  Na **Home** w karcie **wdrożenia** grupy, wybierz **Wdróż**.

4.  W **wdrożenia zasad zgodności** okno dialogowe Wybierz **Przeglądaj** aby wybrać kolekcję użytkowników, do których chcesz wdrożyć zasady.

     Ponadto można wybrać opcje do generowania alertów, gdy zasady nie jest zgodne, a także ustawić harmonogram, według której ta zasada ma zostać obliczone dla zgodności.

5.  Gdy skończysz, wybierz **OK**.

## <a name="monitor-the-compliance-policy"></a>Monitorowanie zasad zgodności

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Aby wyświetlić wyniki zgodności w konsoli programu Configuration Manager

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.

2.  W **monitorowanie** obszaru roboczego, wybierz **wdrożeń**.

3.  Na liście **Wdrożenia** wybierz wdrożenie zasad zgodności, dla którego chcesz przejrzeć informacje o zgodności.

4.  Podsumowanie informacji o zgodności wdrożenia zasad można przejrzeć na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie, a następnie na **Home** w karcie **wdrożenia** grupy, wybierz **Wyświetl stan** otworzyć **stan wdrożenia** strony.

    **Stan wdrożenia** strona zawiera następujące karty:

    -   **Zgodny z**. Pokazuje zgodności zasad na podstawie liczby zasobów, których to dotyczy. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które są zgodne z tą regułą. **Szczegóły zasobu** okienko zawiera użytkowników lub urządzeń, które są zgodne z zasadami. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dodatkowe informacje.

    -   **Błąd**. Przedstawia listę wszystkich błędów dla wybranych zasad wdrożenia na podstawie liczby zasobów, których to dotyczy. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzenia generujące błędy z tą regułą. Po wybraniu użytkownika lub urządzenia, **szczegóły zasobu** okienko zawiera użytkowników lub urządzeń, których dotyczy problem. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dodatkowe informacje o problemie.

    -   **Niezgodny**. Przedstawia listę wszystkich niezgodnych zasad w zasadach, na podstawie liczby zasobów, których to dotyczy. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które nie są zgodne z tą regułą. Po wybraniu użytkownika lub urządzenia, **szczegóły zasobu** okienko zawiera użytkowników lub urządzeń, których dotyczy problem. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dalsze informacje o problemie.

    -   **Nieznany**. Przedstawia listę wszystkich użytkowników i urządzeń, którzy nie zgłosili zgodności dla wdrożenia wybranych zasad, wraz z bieżącym stanem klienta urządzeń.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Do monitorowania stanu zgodności poszczególnych urządzeń

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** obszaru roboczego.

2.  Wybierz **urządzeń**.

3.  Kliknij prawym przyciskiem myszy jednej z kolumn, aby umożliwić większą liczbę kolumn.

  Można dodać następujące kolumny:

  - **Identyfikator urządzenia w usłudze Azure Active Directory**.  Unikatowy identyfikator urządzenia w usłudze Azure Active Directory.

  - **Szczegóły błędu zgodności**.  Szczegóły komunikatu o błędzie podczas procesu end-to-end się nie powiedzie. Jeśli ta kolumna jest pusta, oznacza to, nie znaleziono żadnych błędów i pomyślnie zgłoszono stan zgodności.

  - **Lokalizacja błąd zgodności**.  Więcej informacji na temat których zgodności nie powiodło się. Jeśli ta kolumna jest pusta, oznacza to, nie znaleziono żadnych błędów i pomyślnie zgłoszono stan zgodności. Przykłady, gdzie może się nie powieść procesu zgodności: 
      - Klient programu ConfigMgr
      - Punkt zarządzania
      - Intune
      - Azure Active Directory
<br></br>
  - **Czas oceny zgodności**. Czas ostatniego sprawdzane zgodności.

  - **Zgodność ustawić czas**. Czas ostatniej aktualizacji zgodności w usłudze Azure Active Directory.

  - **Zgodny z dostępu warunkowego**.  Określa, czy komputer spełnia zasady dostępu warunkowego.

  > [!IMPORTANT]
  > Domyślnie nie są wyświetlane następujące kolumny.

#### <a name="to-view-intune-compliance-policies-charts"></a>Aby wyświetlać wykresy zasadami zgodności usługi Intune
1. Począwszy od wersji 1610 programu Configuration Manager w konsoli programu Configuration Manager, wybierz **monitorowanie**.

2. W **monitorowanie** obszaru roboczego, przejdź do **Przegląd** > **ustawień zgodności** > **zasady zgodności**.

   Wyświetlane są następujące wykresów:

    - **Ogólna zgodność urządzeń**. Przedstawia ogólną zgodność urządzeń dla wszystkich zasad zgodności.
    - **TOP przyczyn braku zgodności**. Pokazuje pierwsze zasady dla urządzeń, które nie są zgodne.

3. Wybierz sekcję albo wykresu w celu przejścia do listy urządzeń w tej kategorii.

#### <a name="to-view-a-health-attestation-report"></a>Aby wyświetlić raport zaświadczania kondycji

1.  Począwszy od wersji 1602 programu Configuration Manager w konsoli programu Configuration Manager, wybierz **monitorowanie**.

2.  Aby wyświetlić raport z podsumowaniem bieżącego stanu urządzenia według ich stanu zgodności, wybierz **zabezpieczeń**, a następnie wybierz **zaświadczania kondycji**.

3.  Aby wyświetlić raport, który zawiera wszystkie urządzenia i wszystkie atrybuty zaświadczania kondycji, wybierz **zabezpieczeń**, a następnie wybierz **zaświadczania kondycji**.

## <a name="compliance-policy-rules"></a>Reguły zasad zgodności
* **Wymagaj ustawień haseł na urządzeniach przenośnych**. Możesz wymagać od użytkowników wprowadzania hasła podczas uzyskiwania dostępu do swoich urządzeń.

  **Obsługiwane na:**
    * Windows Phone 8+
    * iOS 6+
    * Android 4.0+
    * Samsung Knox Standard 4.0+

* **Wymagaj hasła w celu odblokowania bezczynności urządzenia** (1602 update). Może wymagać użytkownikom na wprowadzanie hasła dostępu do urządzenia, które jest zablokowany.

  **Obsługiwane na:**
  * Windows Phone 8+
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Liczba minut braku aktywności, zanim będzie wymagane hasło** (1602 update). Można określić czas bezczynności, użytkownik musi ponownie wprowadzić swoje hasło. Ustaw wartość na jedną z dostępnych opcji: **1 minute**, **5 minutes**, **15 minutes**, **30 minutes**, **1 hour**.

  Ta reguła musi być używany z **Wymagaj hasła do odblokowania bezczynności urządzenia**. W tym polu wartość określa, kiedy urządzenie jest uznawany za bezczynności i jest zablokowany. Gdy **Wymagaj hasła do odblokowania bezczynności urządzenia** jest ustawiona na **True**, użytkownik musi wprowadzić hasło, aby uzyskać dostęp do urządzenia zablokowane.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows RT/8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Wymagaj aktualizacji automatycznych** (1602 update). Urządzenia z Windows 8.1 lub nowszym można wymagać, aby automatycznie zainstalować aktualizacje i można określić klasę aktualizacji.

  Wartość powinna być równa **Brak** aby zapobiec do instalacji automatycznej **zalecane** automatycznie zainstalować wszystkie zalecane aktualizacje lub **ważne** zainstalować tylko aktualizacje sklasyfikowane jako ważne.

  **Obsługiwane na:**
  * Windows Phone 8+

* **Zezwalaj na proste hasła**. Możesz pozwolić użytkownikom na tworzenie prostych haseł, takich jak "1234" lub "1111." To ustawienie jest domyślnie wyłączone.

  **Obsługiwane na:**
  * Windows Phone 8+
  * iOS 6+

* **Minimalna długość hasła**. Można określić minimalną liczbę cyfr lub znaków, że hasło użytkownika muszą mieć (6 domyślnie).

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

  >[!NOTE]
  >W przypadku urządzeń z systemem Windows zabezpieczonych przy użyciu konta Microsoft zasady zgodności zakończy się niepowodzeniem, poprawnie Jeśli **minimalna długość hasła** jest większa niż 8 znaków lub jeśli **minimalna liczba zestawów znaków** jest większa niż 2.

* **Szyfrowanie plików na urządzeniu przenośnym**. Może wymagać urządzenia szyfrowania w celu nawiązania połączenia z zasobami. Urządzenia z systemem Windows Phone 8 są szyfrowane automatycznie. Urządzenia z systemem iOS są szyfrowane po skonfigurowaniu ustawienia **Wymagaj ustawień haseł na urządzeniach przenośnych**. To ustawienie jest domyślnie włączone.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Urządzenie nie może mieć złamane zabezpieczenia lub odblokowany dostęp**. Jeśli to ustawienie jest włączone, których zdjęto zabezpieczenia (iOS) lub możliwością urządzenia (Android) nie są zgodne. To ustawienie jest domyślnie wyłączone.

  **Obsługiwane na:**
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Profil poczty e-mail musi być zarządzane przez usługę Intune**. Po ustawieniu tej opcji **tak**, urządzenie musi używać profilu poczty e-mail wdrożony na urządzeniu. Urządzenie jest traktowane jako niezgodne, jeśli profil poczty e-mail nie jest wdrożony w tej samej grupie użytkowników co grupa użytkowników objęta zasadami zgodności.

  Jest traktowane jako niezgodne także wtedy, gdy użytkownik skonfigurował już na urządzeniu konto e-mail zgodne z profilem e-mail usługi Intune wdrożonym na urządzeniu. W takim przypadku usługa Intune nie może zastąpić profilu określonego przez użytkownika i dlatego nie może nim zarządzać. Użytkownik może dostosowania do urządzenia poprzez usunięcie istniejące ustawienia poczty e-mail, co pozwala zainstalować zarządzany profil poczty e-mail usługi Intune.

  Szczegółowe informacje na temat profilów e-mail można znaleźć w artykule [Umożliwianie dostępu do firmowej poczty e-mail przy użyciu profilów poczty e-mail w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn800672.aspx). To ustawienie jest domyślnie wyłączone.

  **Obsługiwane na:**
  * iOS 6+

* **Profil poczty e-mail**. Jeśli **konto E-mail musi być zarządzane przez usługę Intune** jest zaznaczony, wybierz **wybierz** aby wybrać profil poczty e-mail, które urządzenia muszą być zarządzane przez. Ten profil poczty e-mail musi znajdować się na urządzeniu.

  **Obsługiwane na:**
  * iOS 6+

* **Minimalny system operacyjny wymagany**. Gdy urządzenie nie spełnia minimalne wymagania wersji systemu operacyjnego należy określić, jest raportowana jako niezgodna. Zostanie wyświetlone łącze informacje o sposobie uaktualniania. Użytkownik może wybrać uaktualnić swoje urządzenie, po upływie którego będą one mieć możliwość dostępu do zasobów firmy.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Maksymalna wersja systemu operacyjnego dozwolone**. Jeśli urządzenie korzysta z wersji systemu operacyjnego później niż określona w zasadzie, blokuje dostęp do zasobów firmy i użytkownik jest proszony o skontaktuj się z ich administratora IT. Do momentu zmiany zasady umożliwiające wersji systemu operacyjnego tego urządzenia nie można uzyskać dostęp do zasobów firmy.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Wymagaj urządzeń należy podać w dobrej kondycji** (1602 update). Można ustawić zasady wymagające, należy podać urządzeń z systemem Windows 10 w dobrej kondycji w zasadach zgodności nowego lub istniejącego. Jeśli to ustawienie jest włączone, urządzeń z systemem Windows 10 są oceniane za pośrednictwem usługi zaświadczania kondycji (HAS) dla następujących punktów danych:

  - **Jest włączona funkcja BitLocker**. Po włączeniu funkcji BitLocker, urządzenie może chronić dane przechowywane na dysku przed nieautoryzowanym dostępem, gdy system jest wyłączony lub przechodzi do stanu hibernacji.

   Szyfrowanie dysków za pomocą funkcji Windows BitLocker powoduje zaszyfrowanie wszystkich danych przechowywanych na woluminie systemu operacyjnego Windows. Funkcja BitLocker używa go do ochrony systemu operacyjnego i dane użytkownika. Pomaga upewnić się, że komputer nie jest modyfikowany, nawet jeśli pozostanie instalacji nienadzorowanej, zgubienia lub kradzieży.
   
   Jeśli komputer jest wyposażony w zgodny moduł TPM, funkcja BitLocker używa go do zablokowania kluczy szyfrowania służących do ochrony danych. W związku z tym klucze są niedostępne, dopóki moduł TPM nie zweryfikuje stanu komputera.

  - **Włączono integralności kodu**. Integralność kodu to funkcja, która weryfikuje integralność sterownika lub pliku systemowego zawsze wtedy, gdy jest on ładowany do pamięci. Integralności kodu wykrywa, czy plik niepodpisanych sterowników lub system jest ładowana do jądra. Wykrywa także, czy plik systemowy został zmieniony przez złośliwe oprogramowanie, które zostało uruchomione przez konto użytkownika z uprawnieniami administratora.

  - **Bezpieczny rozruch jest włączony**. Po włączeniu Bezpieczny rozruch systemu jest wymuszone do uruchamiania w stanie fabryki zaufane. Ponadto po włączeniu Bezpieczny rozruch podstawowe składniki używane do uruchomienia maszyny musi mieć prawidłowe podpisy kryptograficzne, które są zaufane przez organizację wyprodukowanych urządzenia. Oprogramowanie układowe UEFI sprawdza to, zanim pozwoli na uruchomienie komputera. Jeśli wszystkie pliki zostały naruszone, przerwanie swój podpis, system nie zostanie uruchomiona.

  - **Włączono wcześniejszego uruchomienia ochrony przed złośliwym oprogramowaniem**. To ustawienie dotyczy tylko komputerów. Usługa wczesnej ochrony przed złośliwym kodem (ELAM, early launch anti-malware) zapewnia ochronę komputerów w sieci podczas ich uruchamiania, zanim zostaną zainicjowane sterowniki innych firm.
  
   Ta reguła jest domyślnie wyłączona.

  Aby uzyskać informacje na temat sposobu działania usługi HAS, zobacz [Health Attestation CSP](https://msdn.microsoft.com/library/dn934876.aspx)(Dostawca usługi konfiguracji zaświadczania o kondycji).

  **Obsługiwane na:**
  * System Windows 10 i Windows 10 Mobile

- **Aplikacje, których nie można zainstalować na urządzeniu**. Jeśli użytkownicy zainstalują aplikację z listy niezgodnych administratora aplikacji, będzie mogą być blokowane podczas próby dostępu do firmowej poczty e-mail i innych zasobów firmy, które obsługują dostęp warunkowy. Ta reguła wymaga nazwy aplikacji i identyfikator aplikacji, dodając aplikację do listy niezgodnych zdefiniowane przez administratora. Można również dodać wydawcę aplikacji, ale nie jest to wymagane.

    **Obsługiwane na:**
      * iOS 6+
      * Android 4.0+
      * Samsung Knox Standard 4.0+

### <a name="find-an-app-id"></a>Identyfikator aplikacji

Identyfikator aplikacji jest identyfikator, który unikatowo identyfikuje aplikacji w ramach usług aplikacji firmy Apple i Google. Przykładem jest com.contoso.myapp. Aby znaleźć jeden:

- **Android**
    - Można znaleźć Identyfikatora w usłudze Google Play przechowywać adres URL, który został użyty do utworzenia aplikacji aplikacji. Identyfikator aplikacji przykład: *...? id=com.companyname.appname & hl = en*

- **iOS**
    1. W iTunes przechowywać adres URL, Znajdź numer identyfikacyjny, takiego jak w tym przykładzie: */id875948587? mt = 8*

    2. W przeglądarce sieci web, przejdź do następującego adresu URL, zastępując Numer numer identyfikacyjny, który właśnie znaleziono (w tym przypadku poprzedni przykład): https://itunes.apple.com/lookup?id=875948587

    3. Pobierz i Otwórz plik tekstowy.
  
    4. Wyszukaj tekst **element bundleId**.

    Identyfikator aplikacji przykład: "*element bundleId*": "*com.companyname.appname*" 


