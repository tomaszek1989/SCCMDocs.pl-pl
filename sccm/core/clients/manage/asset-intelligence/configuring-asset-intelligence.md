---
title: "Konfigurowanie analizy zasobów | Dokumentacja firmy Microsoft"
description: "Konfigurowanie analizy zasobów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 08e0382d-de05-4a76-ba5c-7223173f7066
caps.latest.revision: 7
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: d2704e0f93ad9748f7eb06d714b3754463cb3bdb
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-asset-intelligence-in-system-center-configuration-manager"></a>Konfigurowanie analizy zasobów programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Analiza zasobów zapasy i zarządza wykorzystania licencji na oprogramowanie.   

## <a name="steps-to-configure-asset-intelligence"></a>Procedura konfigurowania analizy zasobów  
   

- **Krok 1**: do zbierania danych o zapasach wymagane dla raportów analizy zasobów, należy włączyć agenta klienta zapasów sprzętu, zgodnie z opisem w [sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).
- **Krok 2**: [Włączanie raportowania klasy spisu sprzętu analizy zasobów](#BKMK_EnableAssetIntelligence).  
- **Krok 3**: [Zainstaluj punkt synchronizacji analizy zasobów](#BKMK_InstallAssetIntelligenceSynchronizationPoint)
- **Krok 4**: [Włącz inspekcję zdarzeń logowania Powodzenie](#BKMK_EnableSuccessLogonEvents)  
- **Krok 5**: [Importowanie informacji o licencji oprogramowania](#BKMK_ImportSoftwareLicenseInformation)  
- **Krok 6**: [Skonfigurować zadania obsługi analizy zasobów](#BKMK_ConfigureMaintenanceTasks) 


###  <a name="BKMK_EnableAssetIntelligence"></a> Enable Asset Intelligence hardware inventory reporting classes  
 Aby włączyć analizy zasobów w lokacji programu Configuration Manager, należy włączyć spisu sprzętu co najmniej jeden analizy zasobów klasy raportowania. Te klasy można włączyć na stronie głównej **Analiza zasobów** lub w obszarze roboczym **Administracja** w węźle **Ustawienia klienta** we właściwościach ustawień klienta. Należy użyć jednej z poniższych procedur.  

##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-the-asset-intelligence-home-page"></a>Aby włączyć klasy raportowania spisu sprzętu analizy zasobów na stronie głównej Analiza zasobów  

1.  W konsoli programu Configuration Manager wybierz **zasobów i zgodność** > **analizy zasobów**.  

3.  Na **Home** w karcie **analizy zasobów** grupy, wybierz **edytować klasy spisu**.   

4.  Aby włączyć raportowanie analizy zasobów, zaznacz **Włącz wszystkie klasy raportowania analizy zasobów** lub **włączyć tylko wybrane klasy raportowania analizy zasobów**, a następnie wybierz co najmniej jedną klasę raportowania z klasy wyświetlane.  

    > [!NOTE]  
    >  W raportach analizy zasobów zależnych od klas spisu sprzętu włączonych za pomocą tej procedury dane są wyświetlane dopiero po przeskanowaniu spisu sprzętu i zwróceniu go przez klientów.  


##### <a name="to-enable-asset-intelligence-hardware-inventory-reporting-classes-from-client-settings-properties"></a>Aby włączyć klasy raportowania spisu sprzętu analizy zasobów z poziomu właściwości ustawień klientów  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **ustawień klienta** > **domyślne ustawienia agenta klienta**. Jeśli utworzono niestandardowe ustawienia, można wybrać te, zamiast tego.  

3.  Na **Home** kartę > **właściwości** grupy, wybierz **właściwości**.   

4.  Wybierz **spisu sprzętu** > **ustawić klasy**. .  

5.  Wybierz **Filtruj według kategorii** > **klasy raportowania analizy zasobów**. Lista klas zostanie odświeżona i zostaną wyświetlone tylko klasy raportowania spisu sprzętu analizy zasobów.  

6.  Wybierz co najmniej jedną klasę raportowania z listy.  

    > [!NOTE]  
    >  W raportach analizy zasobów zależnych od klas spisu sprzętu włączonych za pomocą tej procedury dane są wyświetlane dopiero po przeskanowaniu spisu sprzętu i zwróceniu go przez klientów.  
  

###  <a name="BKMK_InstallAssetIntelligenceSynchronizationPoint"></a> Install an Asset Intelligence Synchronization Point  

Rola systemu lokacji punktu synchronizacji analizy zasobów służy do łączenia lokacji programu Configuration Manager do programu System Center Online do synchronizowania informacji o katalogu analizy zasobów. Punkt synchronizacji analizy zasobów można zainstalować tylko w systemie lokacji znajduje się w lokacji najwyższego poziomu w hierarchii programu Configuration Manager i wymaga dostępu do Internetu, aby zsynchronizować z System Center Online za pomocą portu TCP 443.

Oprócz pobierania nowych informacji z katalogu analizy zasobów punkt synchronizacji analizy zasobów umożliwia przekazywanie niestandardowych informacji o tytułach oprogramowania do usługi System Center Online w celu kategoryzacji. Microsoft traktuje wszystkich tytułów oprogramowania przekazane jako informacje publiczne. Upewnij się, Twoje niestandardowe tytuły nie zawierają informacji poufnych lub zastrzeżonych. Aby uzyskać więcej informacji dotyczących żądania kategoryzacji tytułu oprogramowania, zobacz [żądanie aktualizacji katalogu dla tytułów oprogramowania bez kategorii](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_RequestCatalogUpdate).  

##### <a name="to-install-an-asset-intelligence-synchronization-point-site-system-role"></a>Aby zainstalować rolę systemu lokacji punktu synchronizacji analizy zasobów  

1.  W konsoli programu Configuration Manager wybierz **Administracja**> **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

3.  Rola systemu lokacji punktu synchronizacji analizy zasobów należy dodać do nowej lub istniejącej lokacji serwera systemu:  

    -  Dla **nowy serwer systemu lokacji**: Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz serwer systemu lokacji** Aby uruchomić kreatora.   

        > [!NOTE]  
        >  Domyślnie gdy Configuration Manager instaluje rolę systemu lokacji pliki instalacyjne są instalowane na pierwszy dostępny sformatowanym w systemie NTFS dysku twardym, który ma najwięcej wolnego miejsca. Aby uniemożliwić instalowanie na określonych dyskach programu Configuration Manager, Utwórz pusty plik o nazwie No_sms_on_drive.sms i skopiuj go do folderu głównego dysku przed zainstalowaniem serwera systemu lokacji.  

    -  Dla **istniejący serwer systemu lokacji**: Wybierz serwer, na którym chcesz zainstalować rolę systemu lokacji punktu synchronizacji analizy zasobów. Po wybraniu serwera, w okienku szczegółów wyświetli się lista ról systemu lokacji, które są już zainstalowane na serwerze.  

         Na **Home** w karcie **serwera** grupy, wybierz **Dodaj rolę systemu lokacji** Aby uruchomić kreatora.  

4.  Ukończ **ogólne** strony. W przypadku dodawania punktu synchronizacji analizy zasobów do istniejącego serwera systemu lokacji należy sprawdzić wcześniej skonfigurowane wartości.  

5.  Na **Wybór roli systemu** wybierz opcję **punkt synchronizacji analizy zasobów** z listy dostępnych ról.  

6.  Na **ustawienia połączenia punktu synchronizacji analizy zasobów** wybierz **dalej**.  

     Ustawienie **Użyj tego punktu synchronizacji analizy zasobów** jest domyślnie zaznaczone i nie można go skonfigurować na tej stronie. Usługa System Center Online akceptuje ruch sieciowy tylko za pośrednictwem portu TCP 443, dlatego ustawienia **Numer portu SSL** nie można skonfigurować na tej stronie kreatora.  

7.  Opcjonalnie można określić ścieżkę do pliku certyfikatu (pfx) uwierzytelniania System Center Online. Zwykle nie trzeba określać ścieżki do certyfikatu, ponieważ certyfikat połączenia jest udostępniany automatycznie podczas instalacji roli lokacji.  

8.  Na **ustawienia serwera Proxy** strony, określ, czy punkt synchronizacji analizy zasobów ma używać serwera proxy podczas łączenia z programem System Center Online do synchronizacji katalogu oraz poświadczenia używane do łączenia się z serwerem proxy.  

    > [!WARNING]  
    >  Jeśli połączenie z usługą System Center Online wymaga użycia serwera proxy, certyfikat połączenia może również zostać usunięty w przypadku wygaśnięcia hasła konta użytkownika dla konta skonfigurowanego do uwierzytelniania na serwerze proxy.  

9. Na stronie **Harmonogram synchronizacji** określ, czy katalog analizy zasobów ma być synchronizowany zgodnie z harmonogramem. Po włączeniu harmonogramu synchronizacji określ prosty lub niestandardowy harmonogram synchronizacji. Podczas zaplanowanej synchronizacji punkt synchronizacji analizy zasobów łączy się z usługą System Center Online, aby pobrać najnowszy katalog analizy zasobów. Katalog inteligencji zasobów w węźle analiza zasobów w konsoli programu Configuration Manager można synchronizować ręcznie. Kroki procedury można dokonać ręcznej synchronizacji katalogu analizy zasobów [można dokonać ręcznej synchronizacji katalogu analizy zasobów](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md#BKMK_ManuallySynchronizeCatalog) w sekcji [operacje związane z analizą zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).  

10. Ukończ pracę kreatora 

###  <a name="BKMK_EnableSuccessLogonEvents"></a> Enable auditing of success logon events  
 W czterech raportach analizy zasobów są wyświetlane informacje zebrane z dzienników zdarzeń zabezpieczeń systemu Windows na komputerach klienckich. Oto jak skonfigurować ustawienia logowania zasad zabezpieczeń komputera umożliwia inspekcję zdarzeń logowania na powodzenie.  

##### <a name="to-enable-success-logon-event-logging-by-using-a-local-security-policy"></a>Aby włączyć rejestrowanie zdarzeń pomyślnego logowania przy użyciu lokalnych zasad zabezpieczeń  

1.  Na komputerze klienckim programu Configuration Manager wybierz **Start** > **narzędzia administracyjne** > **zasady zabezpieczeń lokalnych**.  

2.  W **zasady zabezpieczeń lokalnych** okna dialogowego **ustawienia zabezpieczeń**, rozwiń węzeł **zasady lokalne**, a następnie wybierz **zasady inspekcji**.  

3.  W okienku wyników kliknij dwukrotnie **Przeprowadź inspekcję zdarzeń logowania**, upewnij się, że **Powodzenie** pole wyboru jest zaznaczone, a następnie wybierz **OK**.  

##### <a name="to-enable-success-logon-event-logging-by-using-an-active-directory-domain-security-policy"></a>Aby włączyć rejestrowanie zdarzeń pomyślnego logowania przy użyciu zasad zabezpieczeń domeny usługi Active Directory  

1.  Na komputerze będącym kontrolerem domeny, wybierz **Start**, wskaż **narzędzia administracyjne**, a następnie wybierz **zasady zabezpieczeń domeny**.  

2.  W **zasady zabezpieczeń lokalnych** okna dialogowego **ustawienia zabezpieczeń**, rozwiń węzeł **zasady lokalne**, a następnie wybierz **zasady inspekcji**.  

3.  W okienku wyników kliknij dwukrotnie **Przeprowadź inspekcję zdarzeń logowania**, upewnij się, że **Powodzenie** pole wyboru jest zaznaczone, a następnie wybierz **OK**.  

###  <a name="BKMK_ImportSoftwareLicenseInformation"></a> Import software license information  
 W poniższych sekcjach opisano procedury niezbędne do importowania zarówno firmy Microsoft, jak i informacje na temat licencjonowania oprogramowania ogólne do bazy danych lokacji programu Configuration Manager za pomocą Kreatora importu licencji oprogramowania. Podczas importowania informacji o licencjach na oprogramowanie do bazy danych lokacji konto na komputerze serwera lokacji wymaga uprawnień **Pełna kontrola** systemu plików NTFS do udziału plików, który służy do importowania informacji o licencjach na oprogramowanie.  

> [!IMPORTANT]  
>  Gdy informacje o licencjach na oprogramowanie są importowane do bazy danych lokacji, istniejące informacje o licencjach zostają zastąpione. Upewnij się, że plik informacji o licencjach używany w kreatorze importowania licencji na oprogramowanie zawiera pełną listę wszystkich informacji o licencjach na oprogramowanie.  

##### <a name="to-import-software-license-information-into-the-asset-intelligence-catalog"></a>Aby zaimportować informacje o licencjach na oprogramowanie do katalogu analizy zasobów  

1.  W **zasobów i zgodność** obszaru roboczego, wybierz **analizy zasobów**.  

2.  Na **Home** w karcie **analizy zasobów** grupy, wybierz **importu licencji na oprogramowanie**.   

4.  Na stronie **Importowanie** określ, czy importowany jest plik licencjonowania zbiorowego firmy Microsoft (MVLS) (xml lub csv) czy plik ogólnego zestawienia licencji (csv). Więcej informacji na temat tworzenia pliku ogólnego zestawienia licencji można znaleźć w sekcji [Create a general license statement information file for import](#BKMK_CreateGeneralLicenseStatement) w dalszej części tego tematu.  

    > [!WARNING]  
    >  Aby pobrać plik licencjonowania zbiorowego firmy Microsoft w formacie csv, który można zaimportować do katalogu analizy zasobów, odwiedź witrynę [Microsoft Volume Licensing Service Center](http://go.microsoft.com/fwlink/p/?LinkId=226547). Aby uzyskać dostęp do tych informacji, musisz mieć zarejestrowane konto w tej witrynie sieci Web. Skontaktuj się z przedstawicielem klienta firmy Microsoft, aby uzyskać informacje na temat sposobu pobierania pliku licencjonowania zbiorowego firmy Microsoft w formacie xml.  

5.  Wprowadź ścieżkę UNC do pliku zestawienia licencji lub wybierz **Przeglądaj** wybrać sieć udostępnionych plików i folderów.  

    > [!NOTE]  
    >  Folder udostępniony powinien być odpowiednio zabezpieczony w celu uniemożliwienia nieupoważnionego dostępu do pliku informacji o licencjach, a konto na komputerze, na którym uruchomiono kreatora, musi mieć uprawnienia Pełna kontrola do udziału zawierającego plik licencji do zaimportowania.  

6. Ukończ pracę kreatora.  

###  <a name="BKMK_CreateGeneralLicenseStatement"></a> Create a general license statement information file for import  
 Ogólne zestawienie licencji można również zaimportować do katalogu analizy zasobów przy użyciu ręcznie utworzonego pliku importowania licencji w formacje pliku rozdzielanego przecinkami (csv).  

> [!NOTE]  
>  Mimo że tylko pola **Nazwa**, **Wydawca**, **Wersja**i **Efektywna ilość** muszą zawierać dane, w pierwszym wierszu pliku importowania licencji należy wprowadzić wszystkie pola. Wszystkie pola Data mają być wyświetlane w następującym formacie: Miesiąc/dzień/rok, na przykład, 2008-08-04.  

Analiza zasobów dopasowuje produkty określone w ogólnym zestawieniu licencji w oparciu o nazwę produktu i wersję produktu, ale nie na podstawie nazwy wydawcy. Należy użyć nazwy produktu w ogólnym zestawieniu licencji, która jest identyczna z nazwą produktu przechowywaną w bazie danych lokacji. Analiza zasobów przyjmuje **EffectiveQuantity** numer podany w instrukcji ogólnych licencji i porównuje liczbę z liczbą zainstalowanych produktów odnaleźć w magazynie programu Configuration Manager.  

> [!TIP]  
>  Aby uzyskać pełną listę nazw produktów, przechowywane w bazie danych lokacji programu Configuration Manager, należy wykonać następujące zapytanie w bazie danych: Wybierz ProductName0 z v_GS_INSTALLED_SOFTWARE.  

 Można określić dokładną wersję lub część wersji produktu, na przykład tylko wersję główną. Poniższe przykłady zapewniają w rezultacie dopasowanie wersji do wpisów wersji w ogólnym zestawieniu licencji dla określonego produktu.  

|Wpis ogólnego zestawienia licencji|Pasujące wpisy w bazie danych lokacji|  
|-------------------------------------|------------------------------------|  
|Nazwa: "MySoftware", ProductVersion0: "2"|ProductName0: "Mysoftware", ProductVersion0: "2.01.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.02.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.10.1234"|  
|Nazwa: "MySoftware", wersja "2.05"|ProductName0: "MySoftware", ProductVersion0: "2.05.1234"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.5678"<br /><br /> ProductName0: "MySoftware", ProductVersion0: "2.05.3579.000"|  
|Nazwa: "Mysoftware", wersja "2"<br /><br /> Nazwa: "Mysoftware", wersja "2.05"|Błąd podczas importowania. Importowanie nie powiedzie się, gdy więcej niż jeden wpis będzie zgodny z tą samą wersją produktu.|  
  

##### <a name="to-create-a-general-license-statement-import-file-by-using-microsoft-excel"></a>Aby utworzyć plik importu ogólnego zestawienia licencji za pomocą programu Microsoft Excel  

1.  Otwórz program Microsoft Excel i utwórz nowy arkusz kalkulacyjny.  

2.  W pierwszym wierszu nowego arkusza kalkulacyjnego wprowadź wszystkie nazwy pól danych licencji na oprogramowanie.  

3.  W drugim i kolejnych wierszach nowego arkusza kalkulacyjnego wprowadź wymagane informacje o licencjach na oprogramowanie. Upewnij się, że przynajmniej wszystkie wymagane pola danych licencji na oprogramowanie są wypełnione w kolejnych wierszach dla każdej licencji na oprogramowanie, która ma zostać zaimportowana. Nazwa tytułu oprogramowania wprowadzona w arkuszu kalkulacyjnym musi być taka sama jak tytuł oprogramowania wyświetlany w Eksploratorze zasobów dla komputera klienckiego po uruchomieniu spisu sprzętu.  

4.  Zapisz plik w formacie CSV.  

5.  Skopiuj plik csv do udziału plików, który służy do importowania informacji o licencjach na oprogramowanie do katalogu analizy zasobów.  

6.  W konsoli programu Configuration Manager należy użyć Kreatora importu licencji oprogramowania do zaimportowania pliku .csv nowo utworzona.  

7.  Uruchom analizy zasobów **licencja 15A - raport uzgadniania oprogramowania innych firm** zweryfikować, czy informacje o licencjonowaniu został pomyślnie zaimportowany do katalogu analizy zasobów.  

> [!NOTE]  
>  Na przykład pliku licencji oprogramowania Ogólne służy do celów testowych, zobacz [pliku importu licencji ogólne przykład analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/example-asset-intelligence-general-license-import.md).  

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
|Data zakupu pomocy technicznej|Wartość bitowa|Nie|0 lub 1: Wprowadź 0 dla tak lub 1 dla nr|  
|Data wygaśnięcia pomocy technicznej|Wartość daty w następującym formacie: MM/DD/RRRR|Nie|Data zakończenia zakupionej pomocy technicznej|  
|Komentarze|Maksymalnie 255 znaków|Nie|Komentarze opcjonalne|  

###  <a name="BKMK_ConfigureMaintenanceTasks"></a> Configure Asset Intelligence maintenance tasks  
 Następujące zadania obsługi są dostępne dla analizy zasobów:  

-   **Sprawdź tytuł aplikacji z informacjami o spisie**: Sprawdza, czy tytuł oprogramowania, który jest zgłaszany w spisie oprogramowania został uzgodniony z tytułem oprogramowania w katalogu analizy zasobów. Domyślnie to zadanie jest włączona i zaplanowane do uruchomienia w sobotę po od 12:00 i przed godziny 5:00 To zadanie konserwacji jest dostępna tylko w lokacji najwyższego poziomu w hierarchii programu Configuration Manager.  

-   **Podsumuj dane zainstalowanego oprogramowania**: Zawiera informacje, które są wyświetlane w **zasoby i zgodność** obszaru roboczego, w **spisane oprogramowanie** węzła w obszarze **analizy zasobów** węzła. Podczas wykonywania zadania programu Configuration Manager gromadzi liczba dla wszystkich tytułów dodawanych do spisu oprogramowania w lokacji głównej. Domyślnie to zadanie jest włączona i zaplanowane do uruchomienia codziennie po od 12:00 i przed godziny 5:00 To zadanie konserwacji jest dostępna tylko w lokacji podstawowej.  

##### <a name="to-configure-asset-intelligence-maintenance-tasks"></a>Aby skonfigurować zadania obsługi analizy zasobów  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz lokację, dla której chcesz skonfigurować zadanie obsługi analizy zasobów.  

4.  Na **Home** w karcie **ustawienia** grupy, wybierz **konserwacja witryny**. Wybierz zadanie, a następnie wybierz **Edytuj** Aby zmodyfikować ustawienia. 

      Zalecane ustawienie czasu do poza godzinami pracy witryny. Okres czasu jest interwałem czasu, w którym zadanie może być uruchamiane. Jest on definiowany przez wartości **Rozpoczęcie po godzinie** i **Najpóźniejsza godzina rozpoczęcia** określone w oknie dialogowym **Właściwości zadania** .  

    Możesz natychmiast zainicjować zadanie, wybierając bieżącą datę i ustawiając czas **Rozpoczęcie po godzinie** na kilka minut po chwili obecnej.  

7.  Wybierz **OK** Aby zapisać ustawienia. Zadanie jest uruchamiane zgodnie ze swoim harmonogramem.  

    > [!NOTE]  
    >  Jeśli zadanie nie powiedzie się przy pierwszej próbie, Configuration Manager próbuje ponownie uruchomić zadanie do momentu zadanie zostanie pomyślnie wykonane lub upłynął okres czasu, w którym można uruchomić zadania.  

