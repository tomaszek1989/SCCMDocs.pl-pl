---
title: Konfigurowanie analizy zasobów
titleSuffix: Configuration Manager
description: Konfigurowanie analizy zasobów w programie System Center Configuration Manager.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 08e0382d-de05-4a76-ba5c-7223173f7066
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 182006f0e4fcaf2304570ef4110527a61180c290
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="configure-asset-intelligence-in-system-center-configuration-manager"></a>Konfigurowanie analizy zasobów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Analiza zasobów umieszczać w spisie i zarządza licencjami na oprogramowanie.   

## <a name="steps-to-configure-asset-intelligence"></a>Procedura konfigurowania analizy zasobów  
   

- **Krok 1**: do zbierania danych spisu wymaganych na potrzeby raportów analizy zasobów, należy włączyć agenta klienta spisu sprzętu zgodnie z opisem w [jak rozszerzyć spis sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).
- **Krok 2**: [Włączanie klas raportowania spisu sprzętu analizy zasobów](#BKMK_EnableAssetIntelligence).  
- **Krok 3**: [Instalowanie punktu synchronizacji analizy zasobów](#BKMK_InstallAssetIntelligenceSynchronizationPoint)
- **Krok 4**: [Włączanie inspekcji zdarzeń pomyślnego logowania](#BKMK_EnableSuccessLogonEvents)  
- **Krok 5**: [Importowanie informacji o licencji oprogramowania](#BKMK_ImportSoftwareLicenseInformation)  
- **Krok 6**: [Konfigurowanie zadań obsługi analizy zasobów](#BKMK_ConfigureMaintenanceTasks) 


###  <a name="BKMK_EnableAssetIntelligence"></a> Enable Asset Intelligence hardware inventory reporting classes  
 Aby włączyć funkcję analizy zasobów w lokacji programu Configuration Manager, należy włączyć co najmniej jeden analizy zasobów klasy raportowania spisu sprzętu. Te klasy można włączyć na stronie głównej **Analiza zasobów** lub w obszarze roboczym **Administracja** w węźle **Ustawienia klienta** we właściwościach ustawień klienta. Użyj jednej z następujących procedur.  

##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-the-asset-intelligence-home-page"></a>Aby włączyć klasy raportowania spisu sprzętu analizy zasobów na stronie głównej Analiza zasobów  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **analizy zasobów**.  

3.  Na **Home** karcie **analizy zasobów** grupy, wybierz **edytowanie klas spisu**.   

4.  Aby włączyć raportowanie analizy zasobów, wybierz **Włącz wszystkie klasy raportowania analizy zasobów** lub **Włącz tylko wybrane klasy raportowania analizy zasobów**, a następnie wybierz co najmniej jedną klasę raportowania z klasy wyświetlane.  

    > [!NOTE]  
    >  W raportach analizy zasobów zależnych od klas spisu sprzętu włączonych za pomocą tej procedury dane są wyświetlane dopiero po przeskanowaniu spisu sprzętu i zwróceniu go przez klientów.  


##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-client-settings-properties"></a>Aby włączyć klasy raportowania spisu sprzętu analizy zasobów z poziomu właściwości ustawień klientów  

1.  W konsoli programu Configuration Manager wybierz **administracji** >  **ustawień klienta** > **domyślne ustawienia agenta klienta**. Jeśli utworzono niestandardowe ustawienia, można wybrać te, zamiast tego.  

3.  Na **Home** kartę > **właściwości** grupy, wybierz **właściwości**.   

4.  Wybierz **spisu sprzętu** > **Ustaw klasy**. .  

5.  Wybierz **Filtruj według kategorii** > **klasy raportowania analizy zasobów**. Lista klas zostanie odświeżona i zostaną wyświetlone tylko klasy raportowania spisu sprzętu analizy zasobów.  

6.  Wybierz co najmniej jedną klasę raportowania z listy.  

    > [!NOTE]  
    >  W raportach analizy zasobów zależnych od klas spisu sprzętu włączonych za pomocą tej procedury dane są wyświetlane dopiero po przeskanowaniu spisu sprzętu i zwróceniu go przez klientów.  
  

###  <a name="BKMK_InstallAssetIntelligenceSynchronizationPoint"></a> Install an Asset Intelligence Synchronization Point  

Rolę systemu lokacji punktu synchronizacji analizy zasobów służy do nawiązania połączenia lokacji programu Configuration Manager System Center Online w celu synchronizowania informacji o katalogu analizy zasobów. Punkt synchronizacji analizy zasobów można zainstalować tylko w systemie lokacji znajduje się w lokacji najwyższego poziomu w hierarchii programu Configuration Manager i wymaga dostępu do Internetu w celu synchronizacji z programem System Center Online przy użyciu portu TCP 443.

Oprócz pobierania nowych informacji z katalogu analizy zasobów punkt synchronizacji analizy zasobów umożliwia przekazywanie niestandardowych informacji o tytułach oprogramowania do usługi System Center Online w celu kategoryzacji. Wszystkie tytuły oprogramowania przekazane są traktowane przez firmę Microsoft jako informacje publiczne. Upewnij się, że niestandardowe tytuły nie zawierają informacji poufnych lub zastrzeżonych. Aby uzyskać więcej informacji na temat żądania kategoryzacji tytułu oprogramowania, zobacz [żądanie aktualizacji katalogu dla tytułów oprogramowania bez kategorii](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_RequestCatalogUpdate).  

##### <a name="to-install-an-asset-intelligence-synchronization-point-site-system-role"></a>Aby zainstalować rolę systemu lokacji punktu synchronizacji analizy zasobów  

1.  W konsoli programu Configuration Manager wybierz **administracji**> **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

3.  Dodaj rolę systemu lokacji punktu synchronizacji analizy zasobów na serwerze systemu lokacji do nowego lub istniejącego:  

    -  Aby uzyskać **nowy serwer systemu lokacji**: Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz serwer systemu lokacji** Aby uruchomić kreatora.   

        > [!NOTE]  
        >  Domyślnie program Configuration Manager instaluje rolę systemu lokacji, pliki instalacyjne są zainstalowane na pierwszy dostępny sformatowanym w systemie NTFS dysku twardym, który ma najwięcej wolnego miejsca. Aby zapobiec instalacji na określonych dyskach programu Configuration Manager, Utwórz pusty plik o nazwie No_sms_on_drive.sms i skopiować go do folderu głównego dysku przed zainstalowaniem serwera systemu lokacji.  

    -  Aby uzyskać **serwera systemu lokacji istniejące**: Wybierz serwer, na którym chcesz zainstalować rolę systemu lokacji punktu synchronizacji analizy zasobów. Po wybraniu serwera, listę ról systemu lokacji, które są już zainstalowane na serwerze są wyświetlane w okienku szczegółów.  

         Na **Home** karcie **serwera** grupy, wybierz **Dodaj rolę systemu lokacji** Aby uruchomić kreatora.  

4.  Zakończenie **ogólne** strony. W przypadku dodawania punktu synchronizacji analizy zasobów do istniejącego serwera systemu lokacji należy sprawdzić wcześniej skonfigurowane wartości.  

5.  Na **Wybór roli systemu** wybierz pozycję **punkt synchronizacji analizy zasobów** z listy dostępnych ról.  

6.  Na **ustawienia połączenia punktu synchronizacji Asset Intelligence** wybierz pozycję **dalej**.  

     Ustawienie **Użyj tego punktu synchronizacji analizy zasobów** jest domyślnie zaznaczone i nie można go skonfigurować na tej stronie. Usługa System Center Online akceptuje ruch sieciowy tylko za pośrednictwem portu TCP 443, dlatego ustawienia **Numer portu SSL** nie można skonfigurować na tej stronie kreatora.  

7.  Opcjonalnie można określić ścieżkę do pliku certyfikatu (pfx) programu System Center Online uwierzytelniania. Zwykle nie trzeba określać ścieżki do certyfikatu, ponieważ certyfikat połączenia jest udostępniany automatycznie podczas instalacji roli lokacji.  

8.  Na **ustawienia serwera Proxy** określ czy punkt synchronizacji analizy zasobów używa serwera proxy podczas nawiązywania połączenia z programem System Center Online do synchronizacji katalogu i czy poświadczenia użyte do nawiązania połączenia z serwerem proxy.  

    > [!WARNING]  
    >  Jeśli połączenie z usługą System Center Online wymaga użycia serwera proxy, certyfikat połączenia może również zostać usunięty w przypadku wygaśnięcia hasła konta użytkownika dla konta skonfigurowanego do uwierzytelniania na serwerze proxy.  

9. Na stronie **Harmonogram synchronizacji** określ, czy katalog analizy zasobów ma być synchronizowany zgodnie z harmonogramem. Po włączeniu harmonogramu synchronizacji określ prosty lub niestandardowy harmonogram synchronizacji. Podczas zaplanowanej synchronizacji punkt synchronizacji analizy zasobów łączy się z usługą System Center Online, aby pobrać najnowszy katalog analizy zasobów. Możesz ręcznie zsynchronizować katalog analizy zasobów z poziomu węzła analiza zasobów w konsoli programu Configuration Manager. Aby uzyskać instrukcje dotyczące ręcznej synchronizacji katalogu analizy zasobów, zobacz [Aby ręcznie zsynchronizować katalog analizy zasobów](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ManuallySynchronizeCatalog) sekcji [operacje związane z analizą zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).  

10. Ukończ pracę kreatora 

###  <a name="BKMK_EnableSuccessLogonEvents"></a> Enable auditing of success logon events  
 W czterech raportach analizy zasobów są wyświetlane informacje zebrane z dzienników zdarzeń zabezpieczeń systemu Windows na komputerach klienckich. Oto, jak skonfigurować ustawienia logowania zasad zabezpieczeń komputera w celu włączenia inspekcji zdarzeń pomyślnego logowania.  

##### <a name="to-enable-success-logon-event-logging-by-using-a-local-security-policy"></a>Aby włączyć rejestrowanie zdarzeń pomyślnego logowania przy użyciu lokalnych zasad zabezpieczeń  

1.  Na komputerze klienckim programu Configuration Manager wybierz **Start** > **narzędzia administracyjne** > **zasady zabezpieczeń lokalnych**.  

2.  W **zasady zabezpieczeń lokalnych** okna dialogowego, w obszarze **ustawienia zabezpieczeń**, rozwiń węzeł **zasady lokalne**, a następnie wybierz pozycję **zasady inspekcji**.  

3.  W okienku wyników kliknij dwukrotnie **Przeprowadź inspekcję zdarzeń logowania**, upewnij się, że **Powodzenie** pole wyboru jest zaznaczone, a następnie wybierz pozycję **OK**.  

##### <a name="to-enable-success-logon-event-logging-by-using-an-active-directory-domain-security-policy"></a>Aby włączyć rejestrowanie zdarzeń pomyślnego logowania przy użyciu zasad zabezpieczeń domeny usługi Active Directory  

1.  Na komputerze będącym kontrolerem domeny, wybierz **Start**, wskaż polecenie **narzędzia administracyjne**, a następnie wybierz pozycję **zasady zabezpieczeń domeny**.  

2.  W **zasady zabezpieczeń lokalnych** okna dialogowego, w obszarze **ustawienia zabezpieczeń**, rozwiń węzeł **zasady lokalne**, a następnie wybierz pozycję **zasady inspekcji**.  

3.  W okienku wyników kliknij dwukrotnie **Przeprowadź inspekcję zdarzeń logowania**, upewnij się, że **Powodzenie** pole wyboru jest zaznaczone, a następnie wybierz pozycję **OK**.  

###  <a name="BKMK_ImportSoftwareLicenseInformation"></a> Import software license information  
 W poniższych sekcjach opisano procedury niezbędne do zaimportowania zarówno informacji firmy Microsoft oraz oprogramowania ogólne licencjonowania w bazie danych lokacji programu Configuration Manager przy użyciu Kreatora importowania licencji na oprogramowanie. Podczas importowania informacji o licencjach na oprogramowanie do bazy danych lokacji konto na komputerze serwera lokacji wymaga uprawnień **Pełna kontrola** systemu plików NTFS do udziału plików, który służy do importowania informacji o licencjach na oprogramowanie.  

> [!IMPORTANT]  
>  Gdy informacje o licencjach na oprogramowanie są importowane do bazy danych lokacji, istniejące informacje o licencjach zostają zastąpione. Upewnij się, że plik informacji o licencjach używany w kreatorze importowania licencji na oprogramowanie zawiera pełną listę wszystkich informacji o licencjach na oprogramowanie.  

##### <a name="to-import-software-license-information-into-the-asset-intelligence-catalog"></a>Aby zaimportować informacje o licencjach na oprogramowanie do katalogu analizy zasobów  

1.  W **zasoby i zgodność** obszaru roboczego wybierz **analizy zasobów**.  

2.  Na **Home** karcie **analizy zasobów** grupy, wybierz **importowania licencji na oprogramowanie**.   

4.  Na stronie **Importowanie** określ, czy importowany jest plik licencjonowania zbiorowego firmy Microsoft (MVLS) (xml lub csv) czy plik ogólnego zestawienia licencji (csv). Więcej informacji na temat tworzenia pliku ogólnego zestawienia licencji można znaleźć w sekcji [Tworzenie pliku ogólnego zestawienia licencji informacje do zaimportowania](#BKMK_CreateGeneralLicenseStatement) w dalszej części tego tematu.  

    > [!WARNING]  
    >  Aby pobrać plik licencjonowania zbiorowego firmy Microsoft w formacie csv, który można zaimportować do katalogu analizy zasobów, odwiedź witrynę [Microsoft Volume Licensing Service Center](http://go.microsoft.com/fwlink/p/?LinkId=226547). Aby uzyskać dostęp do tych informacji, musisz mieć zarejestrowane konto w tej witrynie sieci Web. Skontaktuj się z przedstawicielem klienta firmy Microsoft, aby uzyskać informacje na temat sposobu pobierania pliku licencjonowania zbiorowego firmy Microsoft w formacie xml.  

5.  Wprowadź ścieżkę UNC do pliku zestawienia licencji lub wybierz **Przeglądaj** aby wybrać sieciowy folder udostępniony i plik.  

    > [!NOTE]  
    >  Folder udostępniony powinien być odpowiednio zabezpieczony w celu uniemożliwienia nieupoważnionego dostępu do pliku informacji o licencjach, a konto na komputerze, na którym uruchomiono kreatora, musi mieć uprawnienia Pełna kontrola do udziału zawierającego plik licencji do zaimportowania.  

6. Ukończ pracę kreatora.  

###  <a name="BKMK_CreateGeneralLicenseStatement"></a>Tworzenie pliku ogólnego zestawienia licencji informacje do zaimportowania  
 Ogólne zestawienie licencji można również zaimportować do katalogu analizy zasobów przy użyciu ręcznie utworzonego pliku importowania licencji w formacje pliku rozdzielanego przecinkami (csv).  

> [!NOTE]  
>  Mimo że tylko pola **Nazwa**, **Wydawca**, **Wersja**i **Efektywna ilość** muszą zawierać dane, w pierwszym wierszu pliku importowania licencji należy wprowadzić wszystkie pola. Wszystkie pola dat powinien być wyświetlany w następującym formacie: Miesiąc/dzień/rok, na przykład 08/04/2008.  

Analiza zasobów dopasowuje produkty określone w ogólnym zestawieniu licencji w oparciu o nazwę produktu i wersję produktu, ale nie na podstawie nazwy wydawcy. Należy użyć nazwy produktu w ogólnym zestawieniu licencji, która jest identyczna z nazwą produktu przechowywaną w bazie danych lokacji. Analiza zasobów **efektywna ilość** numer podany w ogólnym zestawieniu licencji i porównuje liczbę z liczbą zainstalowanych produktów znaleziono w magazynie programu Configuration Manager.  

> [!TIP]  
>  Aby uzyskać pełną listę nazw produktów przechowywanych w bazie danych lokacji programu Configuration Manager, można uruchomić następujące zapytanie w bazie danych lokacji: SELECT ProductName0 FROM v_GS_INSTALLED_SOFTWARE.  

 Można określić dokładną wersję lub część wersji produktu, na przykład tylko wersję główną. Poniższe przykłady zapewniają w rezultacie dopasowanie wersji do wpisów wersji w ogólnym zestawieniu licencji dla określonego produktu.  

|Wpis ogólnego zestawienia licencji|Pasujące wpisy w bazie danych lokacji|  
|-------------------------------------|------------------------------------|  
|Nazwa: "Mojeoprogramowanie", ProductVersion0: "2"|ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.01.1234"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.02.5678"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.05.3579.000"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.10.1234"|  
|Nazwa: "Mojeoprogramowanie", Version "2.05"|ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "Mojeoprogramowanie", ProductVersion0: "2.05.3579.000"|  
|Nazwa: "Mojeoprogramowanie", wersja "2"<br /><br /> Nazwa: "Mojeoprogramowanie", Version "2.05"|Błąd podczas importowania. Importowanie nie powiedzie się, gdy więcej niż jeden wpis będzie zgodny z tą samą wersją produktu.|  
  

##### <a name="to-create-a-general-license-statement-import-file-by-using-microsoft-excel"></a>Aby utworzyć plik importu ogólnego zestawienia licencji za pomocą programu Microsoft Excel  

1.  Otwórz program Microsoft Excel i utwórz nowy arkusz kalkulacyjny.  

2.  W pierwszym wierszu nowego arkusza kalkulacyjnego wprowadź wszystkie nazwy pól danych licencji na oprogramowanie.  

3.  W drugim i kolejnych wierszach nowego arkusza kalkulacyjnego wprowadź wymagane informacje o licencjach na oprogramowanie. Upewnij się, że przynajmniej wszystkie wymagane pola danych licencji na oprogramowanie są wypełnione w kolejnych wierszach dla każdej licencji na oprogramowanie, która ma zostać zaimportowana. Nazwa tytułu oprogramowania wprowadzona w arkuszu kalkulacyjnym musi być taka sama jak tytuł oprogramowania wyświetlany w Eksploratorze zasobów dla komputera klienckiego po uruchomieniu spisu sprzętu.  

4.  Zapisz plik w formacie CSV.  

5.  Skopiuj plik csv do udziału plików, który służy do importowania informacji o licencjach na oprogramowanie do katalogu analizy zasobów.  

6.  W konsoli programu Configuration Manager należy użyć Kreatora importowania licencji na oprogramowanie można zaimportować pliku CSV nowo utworzony.  

7.  Uruchom analizę zasobów **licencja 15A - raport uzgadniania oprogramowania innych firm** Aby sprawdzić, czy informacje licencyjne został pomyślnie zaimportowany do katalogu analizy zasobów.  

> [!NOTE]  
>  Na przykład plik licencji ogólne oprogramowania służącego do celów testowych zobacz [plik importu ogólnej licencji analizy zasobów przykład w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md).  

#### <a name="sample-table-to-describe-software-licenses"></a>Przykładowa tabela zawierająca opis licencji na oprogramowanie  
 Podczas tworzenia pliku importu ogólnego zestawienia licencji informacje w poniższej tabeli mogą służyć jako opis licencji na oprogramowanie przeznaczonych do zaimportowania do katalogu analizy zasobów.  

|Nazwa kolumny|Typ danych|Wymagane|Przykład|  
|-----------------|---------------|--------------|-------------|  
|Nazwa|Maksymalnie 255 znaków|Tak|Tytuł oprogramowania|  
|Wydawca|Maksymalnie 255 znaków|Tak|Wydawca oprogramowania|  
|Wersja|Maksymalnie 255 znaków|Tak|Wersja tytułu oprogramowania|  
|Język|Maksymalnie 255 znaków|Tak|Język tytułu oprogramowania|  
|Efektywna ilość|Wartość całkowita|Tak|Liczba zakupionych licencji|  
|Numer zamówienia zakupu|Maksymalnie 255 znaków|Nie|Informacje o zamówieniu zakupu|  
|Nazwa odsprzedawcy|Maksymalnie 255 znaków|Nie|Informacje o odsprzedawcy|  
|Data zakupu|Wartość daty w następującym formacie: MM/DD/RRRR|Nie|Data zakupu licencji|  
|Data zakupu pomocy technicznej|Wartość bitowa|Nie|0 lub 1: Wprowadź 0 dla tak lub 1 dla nie|  
|Data wygaśnięcia pomocy technicznej|Wartość daty w następującym formacie: MM/DD/RRRR|Nie|Data zakończenia zakupionej pomocy technicznej|  
|Komentarze|Maksymalnie 255 znaków|Nie|Komentarze opcjonalne|  

###  <a name="BKMK_ConfigureMaintenanceTasks"></a> Configure Asset Intelligence maintenance tasks  
 Następujące zadania obsługi są dostępne dla analizy zasobów:  

-   **Sprawdź tytuł aplikacji z informacjami o spisie**: Sprawdza, czy tytuł oprogramowania zgłoszony w spisie oprogramowania został uzgodniony z tytułem oprogramowania w katalogu analizy zasobów. Domyślnie to zadanie jest włączone i zaplanowane do uruchomienia w sobotę po 00:00 i przed 05:00. To zadanie obsługi jest dostępna tylko w lokacji najwyższego poziomu w hierarchii programu Configuration Manager.  

-   **Podsumuj dane zainstalowanego oprogramowania**: Zawiera informacje, które są wyświetlane w **zasoby i zgodność** obszaru roboczego w **spisane oprogramowanie** węzła, w obszarze **analizy zasobów** węzła. Po uruchomieniu zadania programu Configuration Manager zbiera informacje o liczbie wszystkich spisanych tytułów oprogramowania w lokacji głównej. Domyślnie to zadanie jest włączone i zaplanowane do uruchomienia codziennie po 00:00 i przed 05:00. To zadanie obsługi jest dostępna tylko w lokacjach głównych.  

##### <a name="to-configure-asset-intelligence-maintenance-tasks"></a>Aby skonfigurować zadania obsługi analizy zasobów  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować zadanie obsługi analizy zasobów.  

4.  Na **Home** karcie **ustawienia** grupy, wybierz **konserwacji lokacji**. Wybierz zadanie, a następnie wybierz pozycję **Edytuj** Aby zmodyfikować ustawienia. 

    Zalecamy ustawienie okresu czasu poza godzinami szczytu witryny. Okres czasu jest interwałem czasu, w którym zadanie może być uruchamiane. Jest on definiowany przez wartości **Rozpoczęcie po godzinie** i **Najpóźniejsza godzina rozpoczęcia** określone w oknie dialogowym **Właściwości zadania** .  

    Możesz natychmiast zainicjować zadanie, wybierając bieżącą datę i ustawiając czas **Rozpoczęcie po godzinie** na kilka minut po chwili obecnej.  

7.  Wybierz **OK** Aby zapisać ustawienia. Zadanie jest uruchamiane zgodnie ze swoim harmonogramem.  

    > [!NOTE]  
    >  Jeśli zadanie nie powiedzie się przy pierwszej próbie, programu Configuration Manager podejmie próbę ponownego uruchomienia zadania, do momentu jego pomyślnym uruchomieniu lub upłynął okres czasu, w którym można uruchomić zadania.  
