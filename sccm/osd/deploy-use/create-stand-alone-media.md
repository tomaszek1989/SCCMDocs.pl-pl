---
title: "Tworzenie nośnika autonomicznego z System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zastosowanie nośników samodzielnych do wdrażania systemu operacyjnego na komputerze bez połączenia do lokacji programu Configuration Manager lub sieci."
ms.custom: na
ms.date: 06/07/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
caps.latest.revision: "21"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 98f902429ad1b9965a0dc4cc2e1bd071ad5c0779
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-stand-alone-media-with-system-center-configuration-manager"></a>Tworzenie nośnika samodzielnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Nośnik samodzielny w programie Configuration Manager zawiera wszystko, co jest wymagane do wdrożenia systemu operacyjnego na komputerze bez połączenia z lokacją programu Configuration Manager lub za pomocą sieci. Należy użyć nośnika autonomicznego z następujących scenariuszy wdrażania systemu operacyjnego:  

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Uaktualnianie systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md)  

Nośnik samodzielny zawiera sekwencję zadań automatyzującą czynności związane z instalowaniem systemu operacyjnego i całą pozostałą wymaganą zawartość, w tym obraz rozruchowy, obraz systemu operacyjnego i sterowniki urządzeń. Ponieważ na nośniku samodzielnym przechowywane są wszystkie składniki wymagane do wdrożenia systemu operacyjnego, przestrzeń dyskowa wymagana przez taki nośnik jest znacznie większa niż w przypadku nośników innych typów. Po utworzeniu nośnika samodzielnego w centralnej lokacji administracyjnej klient pobierze kod przypisanej do niego lokacji z usługi Active Directory. Nośnik samodzielny utworzony w lokacjach podrzędnych automatycznie przypisze klientowi kod danej lokacji.  

##  <a name="BKMK_CreateStandAloneMedia"></a>Tworzenie nośnika samodzielnego  
Przed utworzeniem nośnika autonomicznego przy użyciu Kreatora tworzenia nośnika sekwencji zadań, należy się upewnić, że zostały spełnione następujące warunki:  

### <a name="create-a-task-sequence-to-deploy-an-operating-system"></a>Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego
W ramach nośnika samodzielnego należy określić sekwencję zadań służącą do wdrażania systemu operacyjnego. Aby uzyskać instrukcje dotyczące tworzenia nowej sekwencji zadań, zobacz [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego w programie System Center Configuration Manager](create-a-task-sequence-to-install-an-operating-system.md).

W przypadku nośnika samodzielnego nie są obsługiwane następujące akcje:
- Krok automatycznego stosowania sterowników w sekwencji zadań. Automatyczne stosowanie sterowników urządzeń z katalogu sterowników nie jest obsługiwane, ale można wybrać krok Zastosuj pakiet sterowników, aby udostępnić określony zestaw sterowników dla instalacji systemu Windows.
- Pobierz zawartość pakietu kroku w sekwencji zadań. Informacje o punkcie zarządzania nie jest dostępny na nośniku autonomicznym, w związku z tym krok zakończy się niepowodzeniem próby wyliczenia lokalizacje zawartości.
- Instalacja aktualizacji oprogramowania
- Instalacja oprogramowania przed wdrożeniem systemu operacyjnego.
- Sekwencji zadań wdrożeń systemu operacyjnego.
- Kojarzenie użytkowników z komputerem docelowym w celu obsługi koligacji urządzenia użytkownika
- Pakiet dynamiczny jest instalowany za pomocą zadania instalowania pakietów.
- Aplikacja dynamiczna jest instalowana za pomocą zadania instalowania aplikacji.

> [!NOTE]    
> Jeśli sekwencja zadań wdrożenia systemu operacyjnego obejmuje [zainstaluj pakiet](../../osd/understand/task-sequence-steps.md#BKMK_InstallPackage) kroku i utworzysz nośnik autonomiczny w centralnej lokacji administracyjnej, może wystąpić błąd. W centralnej lokacji administracyjnej nie ma odpowiednich zasad konfiguracji klienta, które są wymagane do włączenia agenta dystrybucji oprogramowania w trakcie wykonywania sekwencji zadań. W pliku CreateTsMedia.log może pojawić się następujący błąd:    
>     
> "Metoda WMI SMS_TaskSequencePackage.GetClientConfigPolicies nie powiodło się (0x80041001)"    
> 
> W przypadku nośnika samodzielnego zawierającego **zainstaluj pakiet** kroku, należy utworzyć nośnik autonomiczny w lokacji głównej, w której jest włączony agent dystrybucji oprogramowania lub dodać [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine) krok po [Zainstaluj system Windows i program ConfigMgr](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) kroku i przed pierwszym **zainstaluj pakiet** kroku w sekwencji zadań. Krok **Uruchom wiersz polecenia** uruchamia polecenie WMIC włączające agenta dystrybucji oprogramowania przed pierwszym uruchomieniem kroku Zainstaluj pakiet. W kroku **Uruchom wiersz polecenia** sekwencji zadań można użyć następującej składni:    
>    
> *WMIC/Namespace:\\ccm_SoftwareDistributionClientConfig ścieżki \root\ccm\policy\machine\requestedconfig NazwaSkładnika utworzyć = "Włącz SWDist" Enabled = "true", LockSettings = "TRUE", PolicySource = "local", PolicyVersion = "1.0" SiteSettingsKey = "1" /NOINTERACTIVE*


> [!IMPORTANT]    
> Jeśli używasz **Zainstaluj system Windows i program ConfigMgr** sekwencji zadań w sekwencji zadań systemu operacyjnego, nie zaznaczaj **Użyj pakietu przedprodukcyjnego klienta, jeśli jest dostępny** ustawienie w przypadku nośnika samodzielnego. Jeśli to ustawienie jest zaznaczone, a pakiet klienta środowiska przedprodukcyjnego jest dostępny, będzie używany na nośniku autonomicznym. Jest to nieobsługiwane. Aby uzyskać więcej informacji o tym ustawieniu, zobacz [Zainstaluj system Windows i program ConfigMgr](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr).


### <a name="distribute-all-content-associated-with-the-task-sequence"></a>Dystrybucja całej zawartości skojarzonej z sekwencją zadań
Należy przeprowadzić dystrybucję całej zawartości wymaganej przez sekwencję zadań do co najmniej jednego punktu dystrybucji. Zawartość ta obejmuje obraz rozruchowy, obraz systemu operacyjnego i inne skojarzone pliki. Kreator zbiera informacje z punktu dystrybucji, w którym tworzy nośnik samodzielny. Musisz mieć uprawnienia do **odczytu** biblioteki zawartości w tym punkcie dystrybucji.  Aby uzyskać więcej szczegółów, zobacz [Dystrybucja zawartości, do której odwołuje się sekwencja zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS).

### <a name="prepare-the-removable-usb-drive"></a>Przygotowanie wymiennego dysku USB
*Dla wymiennego dysku USB:*

Jeśli ma być używany wymienny dysk USB, musi on być podłączony do komputera, na którym uruchomiono kreatora, i być wykrywalny przez system Windows jako urządzenie wymienne. Podczas tworzenia nośnika kreator zapisuje dane bezpośrednio na dysku USB. Nośnik samodzielny korzysta z systemu plików FAT32. Nie można utworzyć nośnika samodzielnego na dysku flash USB zawierającym plik o rozmiarze ponad 4 GB.

### <a name="create-an-output-folder"></a>Tworzenie folderu wyjściowego
*Dla zestawu dysków CD/DVD:*

Przed uruchomieniem Kreatora tworzenia nośnika sekwencji zadań w celu utworzenia nośnika dla zestawu dysków CD lub DVD należy utworzyć folder na pliki wyjściowe kreatora. Nośnik utworzony dla zestawu dysków CD lub DVD jest zapisywany bezpośrednio w folderze w postaci plików ISO.


 Użyj poniższej procedury można utworzyć nośnik samodzielny dla wymiennego dysku USB lub zestawu dysków CD/DVD.  

## <a name="to-create-stand-alone-media"></a>Aby utworzyć nośnik samodzielny  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz nośnik sekwencji zadań** , aby uruchomić Kreatora tworzenia nośnika sekwencji zadań.  

4.  Na stronie **Wybór typu nośnika** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   Wybierz **nośnika samodzielnego**.  

    -   Opcjonalnie, aby zezwolić na wdrożenie systemu operacyjnego bez wprowadzania danych przez użytkownika, wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego**. Po wybraniu tej opcji nie będzie wyświetlany monit o wprowadzenie przez użytkownika informacji o konfiguracji sieci lub opcjonalnych sekwencji zadań. Jednak w przypadku skonfigurowania ochrony hasłem nośnika użytkownik nadal otrzymuje monit o hasło.  

5.  Na stronie **Typ nośnika** określ, czy nośnik jest dyskiem flash czy zestawem dysków CD/DVD, a następnie skonfiguruj następujące opcje:  

    > [!IMPORTANT]  
    >  Nośnik samodzielny korzysta z systemu plików FAT32. Nie można utworzyć nośnika samodzielnego na dysku flash USB zawierającym plik o rozmiarze ponad 4 GB.  

    -   Jeżeli wybrano opcję **Dysk flash USB**, określ dysk, na którym ma być przechowywana zawartość.  

    -   Jeśli wybrano opcję **Zestaw CD/DVD**, należy określić pojemność nośnika oraz nazwę i ścieżkę do plików wyjściowych. Kreator zapisuje pliki wyjściowe do tej lokalizacji. Na przykład:  **\\\servername\folder\outputfile.iso**  

         Jeżeli pojemność nośnika jest zbyt mała do zapisania całej zawartości, tworzonych jest kilka plików, które należy zapisać na wielu dyskach CD lub DVD. Jeżeli jest wymaganych wiele nośników, programu Configuration Manager dodaje kolejny numer do nazwy poszczególnych utworzonych plików wyjściowych. Ponadto jeśli wdrażania aplikacji z systemem operacyjnym, a nie mieści się na jednym nośniku, program Configuration Manager przechowuje aplikacji na kilku nośnikach. Po uruchomieniu nośnika samodzielnego program Configuration Manager monitu o kolejnego nośnika, na którym przechowywana jest aplikacja.   

         > [!IMPORTANT]  
         >  W przypadku wybrania istniejącego obrazu ISO Kreator tworzenia nośnika sekwencji zadań usuwa ten obraz z dysku lub udziału bezpośrednio po przejściu do następnej strony kreatora. Istniejący obraz zostanie usunięty nawet w przypadku anulowania pracy kreatora.  

     Kliknij przycisk **Dalej**.  

6.  Na **zabezpieczeń** , wybierz jedną z następujących ustawień, a następnie kliknij przycisk **dalej**:
    - **Chroń nośnik hasłem**: Wprowadź silne hasło w celu ochrony nośnika. Jeśli określono hasło, aby używać nośnika jest wymagane hasło.  

        > [!IMPORTANT]  
        >  Na nośniku samodzielnym są szyfrowane tylko kroki sekwencji zadań oraz ich zmienne. Pozostała zawartość nośnika nie jest szyfrowana, więc nie należy dodawać do skryptów sekwencji zadań żadnych poufnych informacji. Należy zapisać i wdrożyć wszystkie informacje poufne przy użyciu zmiennych sekwencji zadań.  

    - **Wybierz zakres dat dla tego nośnika autonomicznego identyfikator był prawidłowy** (począwszy od wersji 1702): Ustaw opcjonalne daty rozpoczęcia i wygaśnięcia na nośniku. Te ustawienia są domyślnie wyłączone. Dane są porównywane z czasem systemowym na komputerze przed uruchomieniem nośnika autonomicznego. Gdy czas systemowy jest wcześniejsza niż godzina rozpoczęcia lub późniejsza niż godzina wygaśnięcia, nośnika samodzielnego nie jest uruchomiona. Te opcje są również dostępne za pomocą polecenia cmdlet New-CMStandaloneMedia środowiska PowerShell.
7.  Na **samodzielny dysk CD/DVD** Określ sekwencję zadań, która wdraża system operacyjny, a następnie kliknij pozycję **dalej**. Wybierz **Wykryj skojarzone zależności aplikacji i dodaj je do tego nośnika** można dodać zawartości do nośnika samodzielnego dla zależności aplikacji.
    > [!TIP]
    > Jeśli nie ma zależności oczekiwanego aplikacji, usuń zaznaczenie i ponownie zaznacz **Wykryj skojarzone zależności aplikacji i dodaj je do tego nośnika** ustawienie, aby odświeżyć listę.

    Kreator umożliwi wybranie tylko tych sekwencji zadań, które są skojarzone z obrazem rozruchowym.  

8. Na **aplikacji wybierz** strony (dostępne począwszy od wersji 1702), określ zawartość aplikacji do uwzględnienia jako część pliku multimedialnego, a następnie kliknij przycisk **dalej**.
9. Na **wybór pakietu** strony (dostępne począwszy od wersji 1702), określ zawartość pakietu do uwzględnienia jako część pliku multimedialnego, a następnie kliknij przycisk **dalej**.
10. Na **wybór pakietu sterowników** strony (dostępne począwszy od wersji 1702), określ zawartość pakietu sterowników do uwzględnienia jako część pliku multimedialnego, a następnie kliknij przycisk **dalej**.
11.  Na **punktów dystrybucji** określ punkty dystrybucji zawierające zawartość wymaganą przez sekwencję zadań, a następnie kliknij pozycję **dalej**.  

     Menedżer konfiguracji będą wyświetlane tylko punktów dystrybucji zawierających zawartość. Przed kontynuowaniem należy przeprowadzić dystrybucję całej zawartości skojarzonej z sekwencją zadań (obraz rozruchowy, obraz systemu operacyjnego itp.) do przynajmniej jednego punktu dystrybucji. Po dystrybucji zawartości można albo uruchom ponownie kreatora lub Usuń wszystkie punkty dystrybucji, które już wybrane na tej stronie możesz przejść do poprzedniej strony i następnie z powrotem do **punktów dystrybucji** strony w celu odświeżenia listy punktów dystrybucji. Więcej informacji o dystrybucji zawartości znajduje się w sekcji [Dystrybucja zawartości, do której odwołuje się sekwencja zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS). Aby uzyskać więcej informacji na temat punktów dystrybucji i zarządzania zawartością, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    > [!NOTE]  
    >  Musi mieć **odczytu** uprawnienia do biblioteki zawartości w punktach dystrybucji.  

12. Na stronie **Dostosowywanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Określ zmienne używane przez sekwencję zadań do wdrożenia systemu operacyjnego.  

    -   Określ dowolne polecenia przeduruchomieniowe, które mają zostać uruchomione przed sekwencją zadań. Polecenia przeduruchomieniowe są skryptami lub plikami wykonywalnymi, które mogą prowadzić interakcję z użytkownikiem w środowisku Windows PE przed uruchomieniem sekwencji zadań w celu zainstalowania systemu operacyjnego. Aby uzyskać więcej informacji dotyczących poleceń przeduruchomieniowych nośnika, zobacz [polecenia dla nośnika sekwencji zadań w programie System Center Configuration Manager Przeduruchomieniowe](../understand/prestart-commands-for-task-sequence-media.md).  

         Opcjonalnie wybierz **pliki dla polecenia przeduruchomieniowego** Aby dodać wymagane pliki dla polecenia przeduruchomieniowego.  

        > [!TIP]  
        >  Podczas tworzenia nośnika sekwencji zadań sekwencja zadań zapisuje identyfikator pakietu i przeduruchomieniowy wiersz polecenia, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań do pliku dziennika CreateTSMedia.log na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Możesz przeglądać ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

13. Ukończ pracę kreatora.  

 Pliki nośników samodzielnych (iso) zostaną utworzone w folderze docelowym. Jeśli wybrano opcję **Samodzielny dysk CD/DVD**, możesz teraz skopiować pliki wyjściowe na zestaw dysków CD lub DVD.  

##  <a name="BKMK_StandAloneMediaTSExample"></a>Przykładowa sekwencja zadań dla nośnika samodzielnego  
 Skorzystaj z poniższej tabeli przedstawiono wskazówki pomocne podczas tworzenia sekwencji zadań w celu wdrożenia systemu operacyjnego przy użyciu nośników autonomicznych. Tabela pomoże określić ogólną sekwencję kroków w sekwencji zadań oraz sposób organizowania tych kroków sekwencji zadań w grupach logicznych. Utworzona sekwencja zadań może się różnić od tego przykładu i może zawierać więcej lub mniej kroków sekwencji zadań, jak i grupy.  

> [!NOTE]  
>  Aby utworzyć nośnika autonomicznego należy zawsze używać Kreatora nośnika sekwencji zadań.  

|Grupa lub krok sekwencji zadań|Opis|  
|---------------------------------|-----------------|  
|Przechwyć pliki i ustawienia — **(Nowa grupa sekwencji zadań)**|Umożliwia utworzenie grupy sekwencji zadań. Grupa sekwencji zadań zawiera podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.|  
|Przechwyć ustawienia systemu Windows|Ten krok sekwencji zadań służy do identyfikowania ustawień systemu Microsoft Windows, które są przechwytywane z istniejącego systemu operacyjnego na komputerze docelowym przed ponownym utworzeniem obrazu. Można przechwycić nazwę komputera, informacje o użytkowniku i organizacji oraz ustawienia strefy czasowej.|  
|Przechwyć ustawienia sieci|Ten krok sekwencji zadań umożliwia przechwytywanie ustawień sieci z komputera, który odbiera sekwencję zadań. Oprócz ustawień karty sieciowej można przechwycić członkostwo domeny lub grupy roboczej.|  
|Przechwyć pliki użytkownika i ustawienia — **(Nowa grupa sekwencji zadań podrzędnych)**|Utwórz grupę sekwencji zadań w innej grupie sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do przechwycenia danych o stanie użytkownika z istniejącego systemu operacyjnego na komputerze docelowym przed ponownym utworzeniem obrazu. Tak jak w przypadku początkowo dodanej grupy, ta podgrupa zawiera podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.|  
|Ustaw lokalizację stanu lokalnego|Ten krok sekwencji zadań umożliwia określenie lokalizacji lokalnej za pomocą zmiennej sekwencji zadań ścieżki chronionej. Stan użytkownika jest przechowywany w chronionym katalogu na dysku twardym.|  
|Przechwyć stan użytkownika|Ten krok sekwencji zadań umożliwia przechwytywanie plików użytkownika oraz ustawień, które mają być migrowane do nowego systemu operacyjnego.|  
|Zainstaluj System operacyjny — **(Nowa grupa sekwencji zadań)**|Utwórz następną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do zainstalowania systemu operacyjnego.|  
|Wykonaj ponowny rozruch do systemu Windows PE lub dysku twardego|Ten krok sekwencji zadań umożliwia określenie opcji ponownego uruchomienia komputera, który odbiera sekwencję zadań. Ten krok zapewnia wyświetlenie użytkownikowi komunikatu z informacją o ponownym uruchomieniu komputera, aby umożliwić kontynuowanie instalacji.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSInWinPE** . Jeśli skojarzona wartość jest równa **false** , ten krok sekwencji zadań będzie kontynuowany.|  
|Zastosuj system operacyjny|Ten krok sekwencji zadań umożliwia zainstalowanie obrazu systemu operacyjnego na komputerze docelowym. Ten krok powoduje usunięcie wszystkich plików w danym woluminie (z wyjątkiem plików sterowania specyficzne dla programu Configuration Manager), a następnie stosuje wszystkie obrazy woluminów zawarte w pliku WIM do odpowiednich sekwencyjnych woluminów dysku. Można również określić plik odpowiedzi **Sysprep** w celu skonfigurowania partycji dysku do użycia podczas instalacji.|  
|Zastosuj ustawienia systemu Windows|Ten krok sekwencji zadań umożliwia skonfigurowanie informacji o konfiguracji ustawień systemu Windows dla komputera docelowego. Ustawienia systemu Windows, które można zastosować, to informacje o użytkownikach i organizacji, informacje o kluczu produktu lub licencji, strefa czasowa i hasło administratora lokalnego.|  
|Zastosuj ustawienia sieci|Ten krok sekwencji zadań pozwala określić informacje o konfiguracji sieci lub grupy roboczej dla komputera docelowego. Można również określić, czy komputer korzysta z serwera DHCP, lub statycznie przypisać informacje o adresie IP.|  
|Zastosuj pakiet sterowników|Ten krok sekwencji zadań pozwala udostępnić wszystkie sterowniki urządzeń w pakiecie sterowników dostępnym do użycia podczas instalacji systemu Windows. Wszystkie niezbędne sterowniki urządzeń muszą być zawarte na nośniku autonomicznym.|  
|Konfiguracja systemu operacyjnego - **(Nowa grupa sekwencji zadań)**|Utwórz następną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do zainstalowania klienta programu Configuration Manager.|  
|Zainstaluj system Windows i program ConfigMgr|Ten krok sekwencji zadań należy zainstalować oprogramowanie klienta programu Configuration Manager. Configuration Manager instaluje i rejestruje identyfikator GUID klienta programu Configuration Manager. Niezbędne parametry instalacji można przypisać w oknie **Właściwości instalacji** .|  
|Przywróć pliki użytkownika i ustawienia — **(Nowa grupa sekwencji zadań)**|Utwórz następną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do przywrócenia stanu użytkownika.|  
|Przywróć stan użytkownika|Ten krok sekwencji zadań umożliwia zainicjowanie narzędzia do migracji stanu użytkowników (USMT) w celu przywrócenia stanu i ustawień użytkownika przechwyconych w ramach akcji przechwytywania stanu użytkownika na komputerze docelowym.|  
