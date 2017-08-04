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
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: 6630d0170df22f46f14df241ffd8d48266c69263
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---

# <a name="create-and-deploy-a-device-compliance-policy"></a>Tworzenie i wdrażanie zasad zgodności urządzenia

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


## <a name="create-a-compliance-policy"></a>Tworzenie zasad zgodności

1.  W konsoli programu System Center Configuration Manager wybierz **zasoby i zgodność**.

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **zasady zgodności**.

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz zasady zgodności**.

4.  Na **ogólne** strony kreatora tworzenia zasad zgodności, podaj następujące informacje:

  * **Nazwa**. Wprowadź unikatową nazwę zasady zgodności. Można użyć maksymalnie 256 znaków.

  * **Opis elementu**. Wprowadź opis, który umożliwia identyfikowanie profilu sieci VPN i znalezienie go w konsoli programu Configuration Manager. Można użyć maksymalnie 256 znaków.

  * **Typ zasad zgodności**. Wybierz typ zasad, który ma zostać utworzony, w zależności od tego, czy urządzenie jest zarządzane przez program Configuration Manager. Dotyczy to wersja lub później.<br /><br /> W przypadku urządzeń zarządzanych przez usługę Intune wybierz opcję **Reguły zgodności dla urządzeń zarządzanych bez klienta programu Configuration Manager** . Po wybraniu tej opcji można także wybrać typ platformy, które mają te zasady do zastosowania do.

  * **Waga niezgodności do raportów**. Określ poziom ważności zgłaszany w przypadku oceny tych zasad zgodności jako niezgodnych. Dostępne są następujące poziomy ważności:

     * **Brak**. Urządzenia, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.
     * **Informacje o**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.   
     * **Ostrzeżenie**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.
     * **Krytyczne**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.
     * **Krytyczne ze zdarzeniem**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.      

5.  Na **obsługiwane platformy** wybierz platformy urządzeń, które zostanie obliczone w tych zasad zgodności, lub wybierz pozycję **Zaznacz wszystko** aby wybrać wszystkie platformy urządzeń. Obsługiwane platformy to: Windows 7, Windows 8.1 i Windows 10; Systemu Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 i Windows Server 2016.

6.  Na stronie **Reguły** należy zdefiniować co najmniej jedną regułę definiującą konfigurację urządzenia, która umożliwia ocenienie urządzenia jako zgodnego. Po utworzeniu zasady zgodności niektóre reguły są domyślnie włączone, ale można je edytować lub usunąć. Aby uzyskać pełną listę wszystkich reguł zobacz sekcję "Reguły zasad zgodności" w dalszej części tego tematu.

  > [!NOTE]  
  >  Na komputerach z systemem Windows Windows 8.1 w wersji systemu operacyjnego jest zgłaszana jako 6.3, a nie 8.1. Jeśli ustawiono regułę wersji systemu operacyjnego jest Windows 8.1 dla systemu Windows, następnie urządzenia będzie zgłaszane jako niezgodne nawet wtedy, gdy urządzenie ma Windows 8.1. Upewnij się, że ustawiono prawidłową *zgłosił* wersji systemu Windows dla reguł minimalnej i maksymalnej systemu operacyjnego. Numer wersji musi odpowiadać wersji który **winver** polecenie zwraca. Ten problem nie występuje w przypadku telefonów z systemem Windows. Wersja jest zgłaszana zgodnie z oczekiwaniami jako wersja 8.1. Dla komputerów z systemem Windows w systemie operacyjnym Windows 10, wersja powinna być ustawiona jako **10.0** poszerzonych o numerze kompilacji systemu operacyjnego **winver** polecenie zwraca.

7.  Na **Podsumowanie** strony kreatora przejrzyj ustawienia, które zostały wykonane, a następnie Zakończ pracę kreatora.

 Nowe zasady zostaną wyświetlone w **zasady zgodności** węzła **zasoby i zgodność** obszaru roboczego.

## <a name="deploy-a-compliance-policy"></a>Wdrażanie zasad zgodności

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **zasady zgodności**.

3.  Na **Home** karcie **wdrożenia** grupy, wybierz **Wdróż**.

4.  W **wdrażanie zasad zgodności** oknie dialogowym wybierz **Przeglądaj** aby wybrać kolekcję użytkowników, dla której chcesz wdrożyć zasady.

     Ponadto można wybrać opcje generowania alertów, gdy zasady są niezgodne i ustaw harmonogram, według której ta zasada ma zostać obliczone dla zgodności.

5.  Gdy wszystko będzie gotowe, wybierz pozycję **OK**.

## <a name="monitor-the-compliance-policy"></a>Monitorowanie zasad zgodności

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Aby wyświetlić wyniki zgodności w konsoli programu Configuration Manager

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.

2.  W **monitorowanie** obszaru roboczego wybierz **wdrożeń**.

3.  Na liście **Wdrożenia** wybierz wdrożenie zasad zgodności, dla którego chcesz przejrzeć informacje o zgodności.

4.  Podsumowanie informacji o zgodności wdrożenia zasad można przejrzeć na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie, a następnie na **Home** karcie **wdrożenia** grupy, wybierz **Wyświetl stan** otworzyć **stan wdrożenia** strony.

    **Stan wdrożenia** strona zawiera następujące karty:

    -   **Zgodne**. Pokazuje zgodności zasad na podstawie liczby uwzględnionych zasobów. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które są zgodne z tą regułą. **Szczegóły zasobu** w okienku zostaną wyświetlone użytkowników lub urządzeń, które są zgodne z zasadami. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dodatkowe informacje.

    -   **Błąd**. Przedstawia listę wszystkich błędów dla wybranego wdrożenia zasad na podstawie liczby uwzględnionych zasobów. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które wygenerowały błędy przy użyciu tej reguły. Po wybraniu użytkownika lub urządzenia, **szczegóły zasobu** w okienku zostaną wyświetlone użytkowników lub urządzeń, których dotyczy problem. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dodatkowe informacje o problemie.

    -   **Niezgodne**. Przedstawia listę wszystkich niezgodnych reguł w zasadzie na podstawie liczby uwzględnionych zasobów. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które nie są zgodne z tą regułą. Po wybraniu użytkownika lub urządzenia, **szczegóły zasobu** w okienku zostaną wyświetlone użytkowników lub urządzeń, których dotyczy problem. Kliknij dwukrotnie użytkownika lub urządzenie na liście, aby wyświetlić dalsze informacje o problemie.

    -   **Nieznany**. Przedstawia listę wszystkich użytkowników i urządzeń, które nie zgłosiły zgodności dla wybranego wdrożenia zasad, wraz z bieżącym stanem klienta urządzeń.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Aby monitorować stan zgodności poszczególne urządzenia

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** obszaru roboczego.

2.  Wybierz **urządzeń**.

3.  Kliknij prawym przyciskiem myszy jeden z kolumny, aby umożliwić większą liczbę kolumn.

  Można dodać następujące kolumny:

  - **Identyfikator urządzenia usługi Azure Active Directory**.  Unikatowy identyfikator dla urządzenia w usłudze Azure Active Directory.

  - **Szczegóły błędu zgodności**.  Szczegóły komunikatu o nieprawidłowość procesu end-to-end. Jeśli ta kolumna jest puste, oznacza to, nie znaleziono błędów, a stan zgodności pomyślnie został zgłoszony.

  - **Lokalizacja błąd zgodności**.  Więcej informacji na temat których zgodności nie powiodło się. Jeśli ta kolumna jest puste, oznacza to, nie znaleziono błędów, a stan zgodności pomyślnie został zgłoszony. Przykłady, których proces zgodności może zakończyć się niepowodzeniem: 
      - Klient programu ConfigMgr
      - Punkt zarządzania
      - Intune
      - Usługa Azure Active Directory
<br></br>
  - **Czas oceny zgodności**. Czas ostatniego zaznaczono zgodności.

  - **Zgodność ustawić czas**. Czas ostatniej aktualizacji zgodności do usługi Azure Active Directory.

  - **Dostęp warunkowy zgodne**.  Określa, czy maszyna spełnia zasady dostępu warunkowego.

  > [!IMPORTANT]
  > Domyślnie nie są wyświetlane następujące kolumny.

#### <a name="to-view-intune-compliance-policies-charts"></a>Aby wyświetlić zasadami zgodności usługi Intune wykresy
1. Począwszy od wersji 1610 programu Configuration Manager w konsoli programu Configuration Manager wybierz **monitorowanie**.

2. W **monitorowanie** obszaru roboczego, przejdź do **omówienie** > **ustawień zgodności** > **zasady zgodności**.

   Są wyświetlane wykresy następujące:

    - **Ogólna zgodność urządzenia**. Przedstawia ogólną zgodność urządzeń dla wszystkich zasad zgodności.
    - **Z góry przyczyn braku zgodności**. Pokazuje top zasady dla urządzeń, które są niezgodne.

3. Wybierz sekcję albo wykresie, aby przejść do szczegółów w dół listę urządzeń w ramach tej kategorii.

#### <a name="to-view-a-health-attestation-report"></a>Aby wyświetlić raport zaświadczania o kondycji

1.  Począwszy od wersji 1602 programu Configuration Manager w konsoli programu Configuration Manager wybierz **monitorowanie**.

2.  Aby wyświetlić raport zawierający podsumowanie bieżącego stanu urządzeń według ich stanu zgodności, wybierz **zabezpieczeń**, a następnie wybierz pozycję **zaświadczania o kondycji**.

3.  Aby wyświetlić raport zawierający listę wszystkich urządzeń i wszystkich atrybutów zaświadczania o kondycji, należy wybrać **zabezpieczeń**, a następnie wybierz pozycję **zaświadczania o kondycji**.

## <a name="compliance-policy-rules"></a>Reguły zasad zgodności
* **Wymagaj ustawień haseł na urządzeniach przenośnych**. Można wymagać od użytkowników podania hasła przed uzyskaniem dostępu do swoich urządzeń.

  **Obsługiwane na:**
    * Windows Phone 8+
    * iOS 6+
    * Android 4.0+
    * Samsung Knox Standard 4.0+

* **Wymagaj hasła do odblokowania bezczynnego urządzenia** (aktualizacja 1602). Można wymagać od użytkowników podania hasła do dostępu do zablokowanego urządzenia.

  **Obsługiwane na:**
  * Windows Phone 8+
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Liczba minut braku aktywności, zanim będzie wymagane hasło** (aktualizacja 1602). Można określić czas bezczynności, po użytkownik musi ponownie wprowadzić swoje hasło. Ustaw wartość na jedną z dostępnych opcji: **1 minute**, **5 minutes**, **15 minutes**, **30 minutes**, **1 hour**.

  Ta reguła musi być używany z **Wymagaj hasła do odblokowania bezczynnego urządzenia**. W tym miejscu wartość określa, kiedy urządzenie jest uznawane za bezczynności i jest zablokowany. Gdy **Wymagaj hasła do odblokowania bezczynnego urządzenia** ustawiono **True**, użytkownik musi wprowadzić hasło dostępu do zablokowanego urządzenia.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows RT/8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Wymagaj aktualizacji automatycznych** (aktualizacja 1602). Urządzenia z Windows 8.1 lub nowszym można wymagać, aby automatycznie zainstalować aktualizacje, a następnie można określić klasę aktualizacji.

  Powinien mieć ustawioną wartość **Brak** zapobiegające do instalacji automatycznej **zalecane** Aby automatycznie zainstalować wszystkie zalecane aktualizacje lub **ważne** można zainstalować tylko aktualizacje sklasyfikowane jako ważne.

  **Obsługiwane na:**
  * Windows Phone 8+

* **Zezwalaj na proste hasła**. Można zezwolić użytkownikom na tworzenie prostych haseł, takich jak "1234" lub "1111". To ustawienie jest domyślnie wyłączona.

  **Obsługiwane na:**
  * Windows Phone 8+
  * iOS 6+

* **Minimalna długość hasła**. Można określić minimalną liczbę cyfr lub znaków, że hasło użytkownika musi mieć (6 domyślnie).

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

  >[!NOTE]
  >Dla urządzeń z systemem Windows, które są zabezpieczone przy użyciu konta Microsoft, sprawdzanie zasad zgodności będzie zakończy się niepowodzeniem, jeśli **minimalna długość hasła** jest większa niż 8 znaków lub, jeśli **minimalna liczba zestawów znaków** jest większa niż 2.

* **Szyfrowanie plików na urządzeniu przenośnym**. Może wymagać zaszyfrowania w celu łączenia się z zasobami urządzenia. Urządzenia z systemem Windows Phone 8 są szyfrowane automatycznie. Urządzenia z systemem iOS są szyfrowane po skonfigurowaniu ustawienia **Wymagaj ustawień haseł na urządzeniach przenośnych**. To ustawienie jest domyślnie włączone.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Urządzenie nie może być zdjęte zabezpieczenia lub odblokowany dostęp**. Jeśli to ustawienie zostanie włączone, których zdjęto zabezpieczenia (iOS) lub z odblokowanym (Android) nie są zgodne. To ustawienie jest domyślnie wyłączona.

  **Obsługiwane na:**
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Profil poczty e-mail musi być zarządzane przez usługę Intune**. Po ustawieniu tej opcji **tak**, urządzenie musi używać profilu poczty e-mail wdrożony na urządzeniu. Urządzenie jest traktowane jako niezgodne, jeśli profil poczty e-mail nie jest wdrożony w tej samej grupie użytkowników co grupa użytkowników objęta zasadami zgodności.

  Jest traktowane jako niezgodne także wtedy, gdy użytkownik skonfigurował już na urządzeniu konto e-mail zgodne z profilem e-mail usługi Intune wdrożonym na urządzeniu. W takim przypadku usługa Intune nie może zastąpić profilu określonego przez użytkownika i dlatego nie może nim zarządzać. Użytkownik może Uzgodnij urządzenia przez usunięcie istniejące ustawienia poczty e-mail, co pozwala zainstalować zarządzany profil poczty e-mail usługi Intune.

  Szczegółowe informacje na temat profilów e-mail można znaleźć w artykule [Umożliwianie dostępu do firmowej poczty e-mail przy użyciu profilów poczty e-mail w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn800672.aspx). To ustawienie jest domyślnie wyłączona.

  **Obsługiwane na:**
  * iOS 6+

* **Profil poczty e-mail**. Jeśli **konto E-mail musi być zarządzane przez usługę Intune** jest wybrana, wybierz **wybierz** aby wybrać profil poczty e-mail, którego urządzenia muszą być zarządzane przez. Ten profil poczty e-mail musi znajdować się na urządzeniu.

  **Obsługiwane na:**
  * iOS 6+

* **Wymagana minimalna wersja systemu operacyjnego**. Jeśli urządzenie nie spełnia wymagań minimalnej wersji systemu operacyjnego, określonym przez użytkownika, są zgłaszane jako niezgodne. Zostanie wyświetlony link ze wskazówkami dotyczącymi uaktualniania. Użytkownik może wybrać na uaktualnienie swojego urządzenia, po którym będą oni mogli dostęp do zasobów firmy.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Dozwolona maksymalna wersja systemu operacyjnego**. Jeśli urządzenie korzysta z wersji systemu operacyjnego późniejszej niż określona w regule, to zablokowanie dostępu do zasobów firmy i wyświetlenie monitu do kontaktowania się z administratorem IT. Do momentu zmiany reguły dopuszczającej daną wersję systemu operacyjnego, to urządzenie nie może służyć do dostępu do zasobów firmy.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Wymagaj, aby urządzenia były zgłaszane jako w dobrej kondycji** (aktualizacja 1602). Można ustawić regułę wymagającą, że urządzeń systemu Windows 10 zgłoszenia dobrej kondycji w zasadach zgodności nowego lub istniejącego. Jeśli to ustawienie zostanie włączone, urządzenia systemu Windows 10 są oceniane za pośrednictwem usługi zaświadczania o kondycji (HAS) dla następujących punktów danych:

  - **Funkcja BitLocker jest włączona**. Po włączeniu funkcji BitLocker urządzenie może chronić dane przechowywane na dysku przed nieautoryzowanym dostępem, gdy system jest wyłączony lub zahibernowany.

   Szyfrowanie dysków za pomocą funkcji Windows BitLocker powoduje zaszyfrowanie wszystkich danych przechowywanych na woluminie systemu operacyjnego Windows. Funkcja BitLocker używa modułu TPM do ochrony systemu operacyjnego i danych użytkownika. Pomaga upewnić się, że komputer nie jest modyfikowany, nawet wtedy, gdy zostanie pozostawiony bez nadzoru, utracone lub skradzione.
   
   Jeśli komputer jest wyposażony w zgodny moduł TPM, funkcja BitLocker używa go do zablokowania kluczy szyfrowania służących do ochrony danych. W związku z tym klucze są niedostępne, dopóki moduł TPM nie zweryfikuje stanu komputera.

  - **Włączono integralność kodu**. Integralność kodu to funkcja, która weryfikuje integralność sterownika lub pliku systemowego zawsze wtedy, gdy jest on ładowany do pamięci. Funkcja integralności kodu wykrywa, czy do jądra jest ładowany niepodpisany plik sterownika lub systemu. Wykrywa także, czy plik systemowy został zmieniony przez złośliwe oprogramowanie, które zostało uruchomione przez konto użytkownika z uprawnieniami administratora.

  - **Bezpieczny rozruch jest włączony**. Gdy jest włączona funkcja bezpiecznego rozruchu, system musi włączać się do uruchamiania w fabrycznie zaufanego stanu. Ponadto gdy jest włączona funkcja bezpiecznego rozruchu, podstawowe składniki używane do uruchomienia maszyny musi mieć prawidłowe podpisy kryptograficzne, które są zaufane przez organizację, która wyprodukowała urządzenie. Oprogramowanie układowe UEFI sprawdza to, zanim pozwoli na uruchomienie komputera. Jeśli wszystkie pliki zostały naruszone, spowodowało uszkodzenie ich podpisu, system nie zostanie uruchomiona.

  - **Usługa wczesnej ochrony przed złośliwym kodem jest włączona**. To ustawienie ma zastosowanie tylko do komputerów. Usługa wczesnej ochrony przed złośliwym kodem (ELAM, early launch anti-malware) zapewnia ochronę komputerów w sieci podczas ich uruchamiania, zanim zostaną zainicjowane sterowniki innych firm.
  
   Ta reguła jest domyślnie wyłączona.

  Aby uzyskać informacje na temat sposobu działania usługi HAS, zobacz [Health Attestation CSP](https://msdn.microsoft.com/library/dn934876.aspx)(Dostawca usługi konfiguracji zaświadczania o kondycji).

  **Obsługiwane na:**
  * Windows 10 i Windows 10 Mobile

- **Aplikacje, których nie można zainstalować na urządzeniu**. Jeśli użytkownicy zainstalują aplikację z listy admin niezgodnych aplikacji, będzie mogą być blokowane podczas próby dostępu do firmowej poczty e-mail i innych zasobów firmy, które obsługują dostęp warunkowy. Ta zasada wymaga nazwy aplikacji i identyfikator aplikacji, podczas dodawania aplikacji do listy niezgodnych zdefiniowane przez administratora. Można również dodać wydawcę aplikacji, ale nie jest to wymagane.

    **Obsługiwane na:**
      * iOS 6+
      * Android 4.0+
      * Samsung Knox Standard 4.0+
<br></br>
* **Wymagany typ hasła**. Określ, czy użytkownik muszą utworzyć hasła alfanumerycznego i numeryczne hasła. Alfanumeryczne haseł również określić minimalną liczbę zestawów znaków, które muszą mieć hasłem. Są cztery zestawy znaków: Małe litery, wielkie litery, symbole i cyfry.

    **Obsługiwane na:**
    * Windows Phone 8+
    * Windows 8.1 +
    * iOS 6+
<br></br>
* **Debugowanie USB bloku na urządzeniu**. Nie masz ustawień jako debugowanie USB już jest wyłączona w systemie Android pracy urządzeń.

    **Obsługiwane na:**
    * Android 4.0+
    * Samsung Knox Standard 4.0+
<br></br>
* **Blokowanie aplikacji z nieznanych źródeł**. Wymagaj, aby urządzenia uniemożliwiały instalację aplikacji z nieznanych źródeł. Nie masz Skonfiguruj to ustawienie, jak Android pracy urządzeń zawsze ograniczyć instalacja z nieznanych źródeł.

    **Obsługiwane na:**
    * Android 4.0+
    * Samsung Knox Standard 4.0+
<br></br>
* **Wymagaj skanowania zagrożeń na aplikacje**. To ustawienie określa, że funkcja aplikacji Sprawdź, czy jest włączona na urządzeniu. 

    **Obsługiwane na:**
    * System android 4.2 za pośrednictwem 4.4
    * Samsung Knox Standard 4.0+

### <a name="find-an-app-id"></a>Znajdź identyfikator aplikacji

Identyfikator aplikacji jest identyfikatorem, który unikatowo identyfikuje aplikację w ramach usługi aplikacji firmy Apple i Google. Przykładem jest com.contoso.myapp. Aby określić, co:

- **Android**
    - Można znaleźć aplikacji o identyfikatorze w witrynie Google Play przechowywania adresu URL, którego użyto do utworzenia aplikacji. Identyfikator jest przykładową aplikację: *...? id=com.companyname.appname & hl = en*

- **iOS**
    1. W iTunes przechowywania adresu URL, Znajdź identyfikator, tak jak w tym przykładzie: */id875948587? mt = 8*

    2. W przeglądarce sieci web, przejdź do następującego adresu URL, zastępując numer identyfikator, który właśnie znaleziono (w tym przypadku poprzedniego przykładu): https://itunes.apple.com/lookup?id=875948587

    3. Pobierz i Otwórz plik tekstowy.
  
    4. Wyszukaj tekst **element bundleId**.

    Identyfikator jest przykładową aplikację: "*element bundleId*": "*com.companyname.appname*" 


