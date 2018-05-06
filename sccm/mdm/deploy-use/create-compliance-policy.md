---
title: Tworzenie i wdrażanie zasad zgodności urządzenia
titleSuffix: Configuration Manager
description: Dowiedz się, jak utworzyć i wdrożyć zasady zgodności urządzeń w programie System Center Configuration Manager.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 0fd76043-d7ee-423d-8c5f-aa7e9ed58ce0
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: noindex
ms.openlocfilehash: 3dd502e8ba9e03851af6ec58ad63d4aa805fe7b4
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-and-deploy-a-device-compliance-policy"></a>Tworzenie i wdrażanie zasad zgodności urządzenia

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


## <a name="create-a-compliance-policy"></a>Tworzenie zasad zgodności

1.  W konsoli programu System Center Configuration Manager wybierz **zasoby i zgodność**.

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **zasady zgodności**.

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz zasady zgodności**.

4.  Na **ogólne** strony kreatora tworzenia zasad zgodności, podaj następujące informacje:

  * **Nazwa** — wprowadź unikatową nazwę zasady zgodności. Można użyć maksymalnie 256 znaków.

  * **Opis elementu** — wprowadź ogólny opis profilu sieci VPN, ułatwiający identyfikację w konsoli programu Configuration Manager. Można użyć maksymalnie 256 znaków.

  * **Typ zasad zgodności** — wybierz typ zasad, który ma zostać utworzony, w zależności od tego, czy urządzenie jest zarządzane przez program Configuration Manager. <br /><br /> W przypadku urządzeń zarządzanych przez usługę Intune wybierz opcję **Reguły zgodności dla urządzeń zarządzanych bez klienta programu Configuration Manager** . Po wybraniu tej opcji można także wybrać typ platformy, które mają te zasady do zastosowania do.

  * **Waga niezgodności do raportów** — Określ poziom ważności zgłaszany w przypadku tych zasad zgodności jest ocenione jako niezgodne. Dostępne są następujące poziomy ważności:

     * **Brak** — urządzenia, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.
     * **Informacje o** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.   
     * **Ostrzeżenie** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.
     * **Krytyczne** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager.
     * **Krytyczne ze zdarzeniem** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager. **Krytyczne ze zdarzeniem** poziom ważności jest rejestrowany także jako zdarzenie w dzienniku zdarzeń aplikacji systemu Windows.      

5.  Na **obsługiwane platformy** wybierz platformy urządzeń, które będzie można ocenić tych zasad zgodności. Możesz również **Zaznacz wszystko** aby wybrać wszystkie platformy urządzeń. Obsługiwane platformy to: Windows 7, Windows 8.1 i Windows 10; Systemu Windows Server 2008 R2, Windows Server 2012, Windows Server 2012 R2 i Windows Server 2016.

6.  Na stronie **Reguły** należy zdefiniować co najmniej jedną regułę definiującą konfigurację urządzenia, która umożliwia ocenienie urządzenia jako zgodnego. Po utworzeniu zasady zgodności niektóre reguły są domyślnie włączone, ale można edytować lub usunąć te reguły. Aby uzyskać pełną listę wszystkich reguł zobacz sekcję "Reguły zasad zgodności" w dalszej części tego artykułu.

  > [!NOTE]  
  >  Na komputerach z systemem Windows Windows 8.1 w wersji systemu operacyjnego jest zgłaszana jako 6.3, a nie 8.1. Jeśli ustawiono regułę wersji systemu operacyjnego jest Windows 8.1 dla systemu Windows, następnie urządzenia będzie zgłaszane jako niezgodne nawet wtedy, gdy urządzenie ma Windows 8.1. Upewnij się, że ustawiono prawidłową *zgłosił* wersji systemu Windows dla reguł minimalnej i maksymalnej systemu operacyjnego. Numer wersji musi odpowiadać wersji który **winver** polecenie zwraca. Ten problem; nie występuje w telefonach z systemem Windows wersja jest zgłaszana jako 8.1 zgodnie z oczekiwaniami. Dla komputerów z systemem Windows w systemie operacyjnym Windows 10, wersja powinna być ustawiona jako **10.0** poszerzonych o numerze kompilacji systemu operacyjnego **winver** polecenie zwraca.

7.  Na **Podsumowanie** strony kreatora przejrzyj ustawienia, które zostały wykonane, a następnie Zakończ pracę kreatora.

 Nowe zasady zostaną wyświetlone w **zasady zgodności** węzła **zasoby i zgodność** obszaru roboczego.

## <a name="deploy-a-compliance-policy"></a>Wdrażanie zasad zgodności

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.

2.  W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **zasady zgodności**.

3.  Na **Home** karcie **wdrożenia** grupy, wybierz **Wdróż**.

4.  W **wdrażanie zasad zgodności** oknie dialogowym wybierz **Przeglądaj** aby wybrać kolekcję użytkowników, dla której chcesz wdrożyć zasady.

     Ponadto można wybrać opcje generowania alertów, gdy zasady nie jest zgodny i ustaw harmonogram, według której ta zasada ma zostać obliczone dla zgodności.

5.  Gdy wszystko będzie gotowe, wybierz pozycję **OK**.

## <a name="monitor-the-compliance-policy"></a>Monitorowanie zasad zgodności

#### <a name="to-view-compliance-results-in-the-configuration-manager-console"></a>Aby wyświetlić wyniki zgodności w konsoli programu Configuration Manager

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.

2.  W **monitorowanie** obszaru roboczego wybierz **wdrożeń**.

3.  Na liście **Wdrożenia** wybierz wdrożenie zasad zgodności, dla którego chcesz przejrzeć informacje o zgodności.

4.  Podsumowanie informacji o zgodności wdrożenia zasad można przejrzeć na stronie głównej. Aby wyświetlić bardziej szczegółowe informacje, wybierz wdrożenie, a następnie na **Home** karcie **wdrożenia** grupy, wybierz **Wyświetl stan** otworzyć **stan wdrożenia** strony.

    **Stan wdrożenia** strona zawiera następujące karty:

    -   **Zgodne** — przedstawia zgodności zasad na podstawie liczby uwzględnionych zasobów. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które są zgodne z tą regułą. **Szczegóły zasobu** w okienku zostaną wyświetlone użytkowników lub urządzeń, które są zgodne z zasadami. Aby wyświetlić dodatkowe informacje, kliknij dwukrotnie użytkownika lub urządzenie na liście.

    -   **Błąd** — zawiera listę wszystkich błędów dla wybranego wdrożenia zasad na podstawie liczby uwzględnionych zasobów. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które wygenerowały błędy przy użyciu tej reguły. Po wybraniu użytkownika lub urządzenia, **szczegóły zasobu** w okienku zostaną wyświetlone użytkowników lub urządzeń, których dotyczy problem. Aby wyświetlić dodatkowe informacje o problemie, kliknij dwukrotnie użytkownika lub urządzenie na liście.

    -   **Niezgodne** — zawiera listę wszystkich niezgodnych reguł w zasadzie na podstawie liczby uwzględnionych zasobów. Można wybrać zasadę, aby utworzyć tymczasowy węzeł w węźle **użytkowników** lub **urządzeń** węzła **zasoby i zgodność** obszaru roboczego, który zawiera wszystkich użytkowników lub urządzeń, które nie są zgodne z tą regułą. Po wybraniu użytkownika lub urządzenia, **szczegóły zasobu** w okienku zostaną wyświetlone użytkowników lub urządzeń, których dotyczy problem. Aby wyświetlić dalsze informacje o problemie, kliknij dwukrotnie użytkownika lub urządzenie na liście.

    -   **Nieznany** — zawiera listę wszystkich użytkowników i urządzeń, które nie zgłosiły zgodności dla wybranego wdrożenia zasad, wraz z bieżącym stanem klienta urządzeń.

#### <a name="to-monitor-the-compliance-status-of-an-individual-device"></a>Aby monitorować stan zgodności poszczególne urządzenia

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** obszaru roboczego.

2.  Wybierz **urządzeń**.

3. Aby włączyć więcej kolumn, kliknij prawym przyciskiem myszy jednej z kolumn.

  Można dodać następujące kolumny:

  - **Identyfikator urządzenia usługi Azure Active Directory** — Unikatowy identyfikator urządzenia w usłudze Azure Active Directory.

  - **Szczegóły błędu zgodności** — szczegóły komunikatu o błędzie podczas nieprawidłowość procesu. Jeśli ta kolumna jest puste, oznacza to, nie znaleziono błędów, a stan zgodności pomyślnie został zgłoszony.

  - **Lokalizacja błąd zgodności** — więcej informacji, na których zgodności nie powiodło się. Jeśli ta kolumna jest puste, oznacza to, nie znaleziono błędów, a stan zgodności pomyślnie został zgłoszony. Przykłady, których proces zgodności może zakończyć się niepowodzeniem: 
      - Klient programu ConfigMgr
      - Punkt zarządzania
      - Intune
      - Azure Active Directory
<br></br>
  - **Czas oceny zgodności** — czas ostatniego zaznaczono zgodności.

  - **Ustaw czas zgodności** — czas ostatniego zgodności zostało zaktualizowane do usługi Azure Active Directory.

  - **Zgodne dostępu warunkowego** — Określa, czy maszyna spełnia zasady dostępu warunkowego.

  > [!IMPORTANT]
  > Domyślnie nie są wyświetlane następujące kolumny.

#### <a name="to-view-intune-compliance-policies-charts"></a>Aby wyświetlić zasadami zgodności usługi Intune wykresy
1. W konsoli programu Configuration Manager wybierz **monitorowanie**.

2. W **monitorowanie** obszaru roboczego, przejdź do **omówienie** > **ustawień zgodności** > **zasady zgodności**.

   Są wyświetlane wykresy następujące:

    - **Ogólna zgodność urządzenia** — przedstawia ogólną zgodność urządzeń dla wszystkich zasad zgodności.
    - **Najważniejsze przyczyny niezgodności** -Wyświetla top zasady, których urządzenia są niezgodne.

3. Wybierz sekcję albo wykresie, aby przejść do szczegółów w dół listę urządzeń w ramach tej kategorii.

#### <a name="to-view-a-health-attestation-report"></a>Aby wyświetlić raport zaświadczania o kondycji

1. W konsoli programu Configuration Manager wybierz **monitorowanie**.

2.  Aby wyświetlić raport zawierający podsumowanie bieżącego stanu urządzeń według ich stanu zgodności, wybierz **zabezpieczeń**, a następnie wybierz pozycję **zaświadczania o kondycji**.

3.  Aby wyświetlić raport zawierający listę wszystkich urządzeń i wszystkich atrybutów zaświadczania o kondycji, należy wybrać **zabezpieczeń**, a następnie wybierz pozycję **zaświadczania o kondycji**.

## <a name="compliance-policy-rules"></a>Reguły zasad zgodności
* **Wymagaj ustawień haseł na urządzeniach przenośnych** — można wymagać od użytkowników podania hasła przed uzyskaniem dostępu do swoich urządzeń.

  **Obsługiwane na:**
    * Windows Phone 8+
    * iOS 6+
    * Android 4.0+
    * Samsung Knox Standard 4.0+

* **Wymagaj hasła do odblokowania bezczynnego urządzenia** — można wymagać od użytkowników podania hasła do dostępu do zablokowanego urządzenia.

  **Obsługiwane na:**
  * Windows Phone 8+
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Liczba minut braku aktywności, zanim będzie wymagane hasło** — można określić czas bezczynności, po użytkownik musi ponownie wprowadzić swoje hasło. Ustaw wartość na jedną z dostępnych opcji: **1 minuta**, **5 minut**, **15 minut**, **30 minut**, **1 godzina**.

  Ta reguła musi być używany z **Wymagaj hasła do odblokowania bezczynnego urządzenia**. W tym miejscu wartość określa, kiedy urządzenie jest uznawane za bezczynności i jest zablokowany. Gdy **Wymagaj hasła do odblokowania bezczynnego urządzenia** ustawiono **True**, użytkownik musi wprowadzić hasło dostępu do zablokowanego urządzenia.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows RT/8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Wymagaj aktualizacji automatycznych** — urządzenia z Windows 8.1 lub nowszym można wymagać, aby automatycznie zainstalować aktualizacje, a można określić klasę aktualizacji.

  Wartość powinna być równa **Brak** zapobiegające automatycznej instalacji. Ustaw **zalecane** można automatycznie zainstalować wszystkie zalecane aktualizacje. Aby zainstalować tylko aktualizacje sklasyfikowane jako ważne, ustaw **ważne**.

  **Obsługiwane na:**
  * Windows Phone 8+

* **Zezwalaj na proste hasła** — można zezwolić użytkownikom na tworzenie prostych haseł, takich jak "1234" lub "1111." To ustawienie jest domyślnie wyłączona.

  **Obsługiwane na:**
  * Windows Phone 8+
  * iOS 6+

* **Minimalna długość hasła** — można określić minimalną liczbę cyfr lub znaków, że hasło użytkownika musi mieć (6 domyślnie).

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

  >[!NOTE]
  >Dla urządzeń z systemem Windows, które są zabezpieczone przy użyciu konta Microsoft, sprawdzanie zasad zgodności będzie zakończy się niepowodzeniem, jeśli **minimalna długość hasła** jest większa niż 8 znaków lub, jeśli **minimalna liczba zestawów znaków** jest większa niż 2.

* **Szyfrowanie plików na urządzeniu przenośnym** — można urządzenie musi być szyfrowane w celu łączenia się z zasobami. Urządzenia z systemem Windows Phone 8 są szyfrowane automatycznie. Urządzenia z systemem iOS są szyfrowane po skonfigurowaniu ustawienia **Wymagaj ustawień haseł na urządzeniach przenośnych**. To ustawienie jest domyślnie włączone.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Urządzenie nie może być zdjęte zabezpieczenia lub odblokowany dostęp** — Jeśli włączysz to ustawienie, w których zdjęto zabezpieczenia (iOS) lub odblokowanym (Android) nie są zgodne. To ustawienie jest domyślnie wyłączona.

  **Obsługiwane na:**
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Profil poczty e-mail musi być zarządzane przez usługę Intune** — po ustawieniu tej opcji **tak**, urządzenie musi używać profilu poczty e-mail wdrożony na urządzeniu. Urządzenie jest traktowane jako niezgodne, jeśli profil poczty e-mail nie jest wdrożony w tej samej grupie użytkowników co grupa użytkowników objęta zasadami zgodności.

  Jest traktowane jako niezgodne także wtedy, gdy użytkownik skonfigurował już na urządzeniu konto e-mail zgodne z profilem e-mail usługi Intune wdrożonym na urządzeniu. W takim przypadku usługa Intune nie może zastąpić profilu określonego użytkownika i dlatego nie może nim zarządzać. Użytkownik może Uzgodnij urządzenia przez usunięcie istniejącego ustawienia poczty e-mail, co pozwala zainstalować zarządzany profil poczty e-mail usługi Intune.

  Szczegółowe informacje na temat profilów e-mail można znaleźć w artykule [Umożliwianie dostępu do firmowej poczty e-mail przy użyciu profilów poczty e-mail w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn800672.aspx). To ustawienie jest domyślnie wyłączona.

  **Obsługiwane na:**
  * iOS 6+

* **Profil poczty e-mail** — Jeśli **konto E-mail musi być zarządzane przez usługę Intune** jest wybrana, wybierz **wybierz** aby wybrać profil poczty e-mail, którego urządzenia muszą być zarządzane przez. Ten profil poczty e-mail musi znajdować się na urządzeniu.

  **Obsługiwane na:**
  * iOS 6+

* **Wymagana minimalna wersja systemu operacyjnego** — Jeśli urządzenie nie spełnia wymagań minimalnej wersji systemu operacyjnego, określonym przez użytkownika, są zgłaszane jako niezgodne. Zostanie wyświetlony link ze wskazówkami dotyczącymi uaktualniania. Użytkownik może wybrać na uaktualnienie swojego urządzenia, po którym będą oni mogli dostęp do zasobów firmy.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Dozwolona maksymalna wersja systemu operacyjnego** — Jeśli urządzenie korzysta z wersji systemu operacyjnego późniejszej niż określona w regule, to zablokowanie dostępu do zasobów firmy i wyświetlenie monitu do kontaktowania się z administratorem IT. Do momentu zmiany reguły dopuszczającej daną wersję systemu operacyjnego, to urządzenie nie może służyć do dostępu do zasobów firmy.

  **Obsługiwane na:**
  * Windows Phone 8+
  * Windows 8.1
  * iOS 6+
  * Android 4.0+
  * Samsung Knox Standard 4.0+

* **Wymagaj, aby urządzenia były zgłaszane jako w dobrej kondycji** — można ustawić regułę wymagającą, że urządzeń systemu Windows 10 zgłoszenia dobrej kondycji w zasadach zgodności nowego lub istniejącego. Jeśli to ustawienie zostanie włączone, urządzenia systemu Windows 10 są oceniane za pośrednictwem usługi zaświadczania o kondycji (HAS) dla następujących punktów danych:

  - **Funkcja BitLocker jest włączona** — po włączeniu funkcji BitLocker, urządzenie może chronić dane przechowywane na dysku przed nieautoryzowanym dostępem, gdy system jest wyłączony lub zahibernowany.

   Szyfrowanie dysków za pomocą funkcji Windows BitLocker powoduje zaszyfrowanie wszystkich danych przechowywanych na woluminie systemu operacyjnego Windows. Funkcja BitLocker używa modułu TPM do ochrony systemu operacyjnego i danych użytkownika. Pomaga zapewnić, że komputer nie jest modyfikowany, nawet wtedy, gdy zostanie pozostawiony bez nadzoru, utracone lub skradzione.
   
   Jeśli komputer jest wyposażony w zgodny moduł TPM, funkcja BitLocker używa go do zablokowania kluczy szyfrowania służących do ochrony danych. W związku z tym klucze będą niedostępne, dopóki moduł TPM zweryfikuje stanu komputera.

  - **Włączono integralność kodu** -integralności kodu jest funkcją, która weryfikuje integralność pliku sterownika lub systemu zawsze wtedy, gdy jest ładowany do pamięci. Funkcja integralności kodu wykrywa, czy do jądra jest ładowany niepodpisany plik sterownika lub systemu. Wykrywa także, czy plik systemowy został zmieniony przez złośliwe oprogramowanie, które zostało uruchomione przez konto użytkownika z uprawnieniami administratora.

  - **Bezpieczny rozruch jest włączony** — gdy bezpieczny rozruch jest włączony, system musi włączać się do uruchamiania w fabrycznie zaufanego stanu. Ponadto gdy jest włączona funkcja bezpiecznego rozruchu, podstawowe składniki używane do uruchomienia maszyny musi mieć prawidłowe podpisy kryptograficzne, które są zaufane przez organizację, która wyprodukowała urządzenie. Oprogramowanie układowe UEFI sprawdza to, zanim pozwoli na uruchomienie komputera. Jeśli wszystkie pliki zostały naruszone, spowodowało uszkodzenie ich podpisu, system nie zostanie uruchomiona.

  - **Usługa wczesnej ochrony przed złośliwym kodem jest włączona** — to ustawienie ma zastosowanie tylko do komputerów. Usługa wczesnej ochrony przed złośliwym kodem (ELAM, early launch anti-malware) zapewnia ochronę komputerów w sieci podczas ich uruchamiania, zanim zostaną zainicjowane sterowniki innych firm.
  
   Ta reguła jest domyślnie wyłączona.

  Aby uzyskać informacje na temat sposobu działania usługi HAS, zobacz [Health Attestation CSP](https://msdn.microsoft.com/library/dn934876.aspx)(Dostawca usługi konfiguracji zaświadczania o kondycji).

  **Obsługiwane na:**
  * Windows 10 i Windows 10 Mobile

> [!NOTE]
> Począwszy od 1802 Menedżera konfiguracji programu Software Center pokazano, że element zaświadczania o kondycji urządzenia nie jest zgodne z. <!--1235616--> 
![Zgodność urządzenia zaświadczania o kondycji urządzenia w programie Software Center](./media/Software-Center-noncompliant.PNG)


- **Aplikacje, których nie można zainstalować na urządzeniu** — Jeśli użytkownicy zainstalują aplikację z listy admin niezgodnych aplikacji, będzie mogą być blokowane podczas próby dostępu do firmowej poczty e-mail i innych zasobów firmy, które obsługują dostęp warunkowy. Ta zasada wymaga nazwy aplikacji i identyfikator aplikacji, podczas dodawania aplikacji do listy niezgodnych zdefiniowane przez administratora. Można również dodać wydawcę aplikacji, ale nie jest to wymagane.

    **Obsługiwane na:**
      * iOS 6+
      * Android 4.0+
      * Samsung Knox Standard 4.0+
<br></br>
* **Wymagany typ hasła** — Określ, czy użytkownik musi utworzyć hasła alfanumerycznego i numeryczne hasła. Alfanumeryczne haseł również określić minimalną liczbę zestawów znaków, które muszą mieć hasłem. Są cztery zestawy znaków: małe litery, wielkie litery, symbole i cyfry.

    **Obsługiwane na:**
    * Windows Phone 8+
    * Windows 8.1+
    * iOS 6+
<br></br>
* **Debugowanie USB bloku na urządzeniu** — nie należy skonfigurować to ustawienie jako debugowanie USB już jest wyłączona w systemie Android pracy urządzeń.

    **Obsługiwane na:**
    * Android 4.0+
    * Samsung Knox Standard 4.0+
<br></br>
* **Blokowanie aplikacji z nieznanych źródeł** -wymagają, aby urządzenia uniemożliwiały instalację aplikacji z nieznanych źródeł. Nie masz Skonfiguruj to ustawienie, jak Android pracy urządzeń zawsze ograniczyć instalacja z nieznanych źródeł.

    **Obsługiwane na:**
    * Android 4.0+
    * Samsung Knox Standard 4.0+
<br></br>
* **Wymagaj skanowania zagrożeń na aplikacje** — to ustawienie określa, że funkcja aplikacji Sprawdź, czy jest włączona na urządzeniu. 

    **Obsługiwane na:**
    * System android 4.2 za pośrednictwem 4.4
    * Samsung Knox Standard 4.0+

### <a name="find-an-app-id"></a>Znajdź identyfikator aplikacji

Identyfikator aplikacji jest identyfikatorem, który unikatowo identyfikuje aplikację w ramach usługi aplikacji firmy Apple i Google. Przykładem jest com.contoso.myapp. Aby określić, co:

- **Android**
    - Można znaleźć aplikacji o identyfikatorze w witrynie Google Play przechowywania adresu URL, którego użyto do utworzenia aplikacji. Identyfikator jest przykładową aplikację: *...? id=com.companyname.appname & hl = en*

- **iOS**
    1. W iTunes przechowywania adresu URL, Znajdź identyfikator, tak jak w tym przykładzie: */id875948587? mt = 8*

    2. W przeglądarce sieci web przejdź do następującego adresu URL, zastępując numer identyfikator, który został właśnie znaleziono (w tym przypadku poprzedniego przykładu): https://itunes.apple.com/lookup?id=875948587

    3. Pobierz i Otwórz plik tekstowy.
  
    4. Wyszukaj tekst **element bundleId**.

    Identyfikator jest przykładową aplikację: "*element bundleId*": "*com.companyname.appname*" 

