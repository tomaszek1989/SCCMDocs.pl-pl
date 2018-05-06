---
title: Tworzenie nośnika samodzielnego
titleSuffix: Configuration Manager
description: Zastosowanie nośników samodzielnych do wdrażania systemu operacyjnego na komputerze bez połączenia sieciowego.
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: c6b9ccd2-78d9-4f0e-b25a-70d0866300ba
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 35dd110c2566dab945bb0701e113becb3412d65c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-stand-alone-media-with-system-center-configuration-manager"></a>Tworzenie nośnika samodzielnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Nośnik samodzielny w programie Configuration Manager zawiera wszystkie elementy wymagane do wdrożenia systemu operacyjnego (OS) na komputerze bez połączenia sieciowego. Należy użyć nośnika autonomicznego z następujących scenariuszy wdrażania systemu operacyjnego:  

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Uaktualnianie systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md)  

Nośnik samodzielny zawiera sekwencję zadań automatyzującą czynności związane z instalowaniem systemu operacyjnego oraz inną wymaganą zawartość. Treść ta obejmuje obraz rozruchowy, obraz systemu operacyjnego i sterowniki urządzeń. Ponieważ na nośniku samodzielnym przechowywane są wszystkie informacje niezbędne do wdrożenia systemu operacyjnego, wymaga więcej miejsca niż jest to wymagane dla innych typów nośników. Podczas tworzenia nośnika samodzielnego w centralnej lokacji administracyjnej, klient pobiera jego kod przypisanej lokacji z usługi Active Directory. Nośnik samodzielny utworzony w lokacjach podrzędnych automatycznie przypisuje do klienta kodu lokacji dla tej lokacji.  

##  <a name="BKMK_CreateStandAloneMedia"></a> Tworzenie nośnika samodzielnego  
Przed utworzeniem nośnika autonomicznego przy użyciu Kreatora tworzenia nośnika sekwencji zadań, należy się upewnić, że zostały spełnione następujące warunki:  

### <a name="create-a-task-sequence-to-deploy-an-operating-system"></a>Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego
W ramach nośnika samodzielnego należy określić sekwencję zadań służącą do wdrażania systemu operacyjnego. Aby uzyskać instrukcje dotyczące tworzenia nowej sekwencji zadań, zobacz [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego w programie System Center Configuration Manager](create-a-task-sequence-to-install-an-operating-system.md).

W przypadku nośnika samodzielnego nie są obsługiwane następujące akcje:
- **Automatycznie Zastosuj sterowniki** kroku w sekwencji zadań. Nośnik samodzielny nie obsługuje automatyczne stosowanie sterowników urządzeń z katalogu sterowników. Użyj **zastosuj pakiet sterowników** krok, aby udostępnić określony zestaw sterowników dla Instalatora systemu Windows.
- **Pobierz zawartość pakietu** kroku w sekwencji zadań. Informacji punktu zarządzania nie jest dostępny na nośniku autonomicznym, dlatego tego kroku nie powiedzie, próby wyliczenia lokalizacje zawartości.
- Instalacja aktualizacji oprogramowania
- Instalacja oprogramowania przed wdrożeniem systemu operacyjnego.
- Sekwencji zadań wdrożeń systemu operacyjnego.
- Kojarzenie użytkowników z komputerem docelowym w celu obsługi koligacji urządzenia użytkownika
- Pakiet dynamiczny jest instalowany za pomocą **instalowania pakietów** zadań.
- Aplikacja dynamiczna jest instalowana za pomocą **zainstaluj aplikację** zadań.

> [!NOTE]    
> Błąd może wystąpić, jeśli sekwencja zadań obejmuje [zainstaluj pakiet](../../osd/understand/task-sequence-steps.md#BKMK_InstallPackage) kroku i utworzysz nośnik autonomiczny w centralnej lokacji administracyjnej. Centralna lokacja administracyjna nie ma odpowiednich zasad konfiguracji klienta. Te zasady są wymagane do włączenia agenta dystrybucji oprogramowania podczas wykonywania sekwencji zadań. W pliku CreateTsMedia.log może pojawić się następujący błąd:    
>     
> `WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)`    
> 
> W przypadku nośnika samodzielnego zawierającego **zainstaluj pakiet** krok, Utwórz nośnik autonomiczny w lokacji głównej, w której jest włączony agent dystrybucji oprogramowania. 
>
> Możesz też dodać [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine) krokiem [Zainstaluj system Windows i program ConfigMgr](../understand/task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr) kroku i przed pierwszym **zainstaluj pakiet** kroku w sekwencji zadań. **Uruchom wiersz polecenia** krok uruchamia polecenie WMIC włączające agenta dystrybucji oprogramowania przed pierwszym krokiem zainstaluj pakiet:    
>    
> `WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE`


> [!IMPORTANT]    
> Nie zaznaczaj **Użyj pakietu przedprodukcyjnego klienta, jeśli jest dostępny** w **Zainstaluj system Windows i program ConfigMgr** krok sekwencji zadań dla nośnika samodzielnego. Nośnik samodzielny nie obsługuje użycie tego ustawienia. Aby uzyskać więcej informacji o tym ustawieniu, zobacz [Zainstaluj system Windows i program ConfigMgr](/sccm/osd/understand/task-sequence-steps#BKMK_SetupWindowsandConfigMgr).


### <a name="distribute-all-content-associated-with-the-task-sequence"></a>Dystrybucja całej zawartości skojarzonej z sekwencją zadań
Dystrybucja całej zawartości, która jest wymagana przez sekwencję zadań do co najmniej jednego punktu dystrybucji. Treść ta obejmuje obraz rozruchowy, obraz systemu operacyjnego i inne skojarzone pliki. Kreator zbiera informacje z punktu dystrybucji, w którym tworzy nośnik samodzielny. Użytkownik musi mieć uprawnienia do **odczytu** biblioteki zawartości w tym punkcie dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości odwołuje się sekwencja zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS).

### <a name="prepare-the-removable-usb-drive"></a>Przygotowanie wymiennego dysku USB
*Dla wymiennego dysku USB:*

Jeśli używasz wymienny dysk USB połączyć z dysku USB do komputera, na którym uruchomiono kreatora. Dysk USB musi być wykrywalny przez system Windows jako urządzenie wymienne. Podczas tworzenia nośnika kreator zapisuje dane bezpośrednio na dysku USB. Nośnik samodzielny korzysta z systemu plików FAT32. Nie można utworzyć nośnika samodzielnego na dysku flash USB zawierającym plik o rozmiarze ponad 4 GB.

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

    -   Opcjonalnie, aby zezwolić na wdrożenie systemu operacyjnego bez wprowadzania danych przez użytkownika, wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego**. Po wybraniu tej opcji nie będzie wyświetlany monit o wprowadzenie przez użytkownika informacji o konfiguracji sieci lub opcjonalnych sekwencji zadań. Jeśli nośnik jest skonfigurowany do ochrony hasłem, użytkownik nadal otrzymuje monit o podanie hasła.  

5.  Na **typ nośnika** Określ, czy nośnik jest wymienny dysk USB lub zestawu dysków CD/DVD:  

    > [!IMPORTANT]  
    >  Domyślnie nośnik samodzielny korzysta z systemu plików FAT32. Nie można utworzyć nośnik wymienny dysk USB, którego zawartość zawiera plik o rozmiarze ponad 4 GB.  

    -   W przypadku wybrania **dysku wymiennego USB**, określić dysk, na którym ma być przechowywana zawartość.  

        - **Formatuj wymienny dysk USB (FAT32) i jako dysk rozruchowy**: Domyślnie programowi Configuration Manager przygotowywanie dysku USB. Wiele nowych urządzeń z interfejsem UEFI wymagają rozruchowego partycji FAT32. Jednak ten format również limity rozmiaru plików i ogólną pojemność dysku. Jeśli masz już sformatowany i dysk wymienny, wyłącz tę opcję. 

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
7.  Na **samodzielny dysk CD/DVD** Określ sekwencję zadań, która wdraża system operacyjny, a następnie kliknij pozycję **dalej**. Aby dodać zawartość nośnika samodzielnego dla zależności aplikacji, wybierz polecenie **Wykryj skojarzone zależności aplikacji i dodaj je do tego nośnika**.
    > [!TIP]
    > Jeśli nie ma zależności oczekiwanego aplikacji, usuń zaznaczenie i ponownie zaznacz **Wykryj skojarzone zależności aplikacji i dodaj je do tego nośnika** ustawienie, aby odświeżyć listę.

    Kreator umożliwi wybranie tylko tych sekwencji zadań, które są skojarzone z obrazem rozruchowym.  

8. Na **aplikacji wybierz** strony (dostępne począwszy od wersji 1702), określ zawartość aplikacji do uwzględnienia jako część pliku multimedialnego, a następnie kliknij przycisk **dalej**.
9. Na **wybór pakietu** strony (dostępne począwszy od wersji 1702), określ zawartość pakietu do uwzględnienia jako część pliku multimedialnego, a następnie kliknij przycisk **dalej**.
10. Na **wybór pakietu sterowników** strony (dostępne począwszy od wersji 1702), określ zawartość pakietu sterowników do uwzględnienia jako część pliku multimedialnego, a następnie kliknij przycisk **dalej**.
11.  Na **punktów dystrybucji** określ punkty dystrybucji, które zawierają wymaganą zawartość, a następnie kliknij przycisk **dalej**.  

     Program Configuration Manager wyświetli tylko punktów dystrybucji zawierających zawartość. Przeprowadzić dystrybucję całej zawartości skojarzonej z sekwencją zadań do co najmniej jednego punktu dystrybucji przed kontynuowaniem. Po dystrybucji zawartości, należy odświeżyć listy punktów dystrybucji. Usuń wszystkie punkty dystrybucji, które już wybrane na tej stronie możesz przejść do poprzedniej strony, a następnie z powrotem do **punktów dystrybucji** strony. Alternatywnie Uruchom ponownie kreatora. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości odwołuje się sekwencja zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DistributeTS) i [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

    > [!NOTE]  
    >  Musi mieć **odczytu** uprawnienia do biblioteki zawartości w punktach dystrybucji.  

12. Na stronie **Dostosowywanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   Określ zmienne używane przez sekwencję zadań do wdrożenia systemu operacyjnego.  

    -   Określ dowolne polecenia przeduruchomieniowe, które mają zostać uruchomione przed sekwencją zadań. Polecenia przeduruchomieniowe to skrypt lub plik wykonywalny, który jest uruchamiany w środowisku Windows PE przed uruchomieniem sekwencji zadań. Aby uzyskać więcej informacji, zobacz [polecenia dla nośnika sekwencji zadań Przeduruchomieniowe](../understand/prestart-commands-for-task-sequence-media.md).  

         Opcjonalnie wybierz **pliki dla polecenia przeduruchomieniowego** Aby dodać wymagane pliki dla polecenia przeduruchomieniowego.  

        > [!TIP]  
        >  Podczas tworzenia nośnika sekwencji zadań programu Configuration Manager zapisuje identyfikator pakietu i wiersz polecenia przeduruchomieniowego do **CreateTSMedia.log** plik na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Te dane wyjściowe obejmują wartości wszelkich zmiennych sekwencji zadań. Przejrzyj ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

13. Ukończ pracę kreatora.  

 Pliki nośników samodzielnych (iso) zostaną utworzone w folderze docelowym. Jeśli wybrano opcję **Samodzielny dysk CD/DVD**, możesz teraz skopiować pliki wyjściowe na zestaw dysków CD lub DVD.  

##  <a name="BKMK_StandAloneMediaTSExample"></a> Przykładowa sekwencja zadań dla nośnika samodzielnego  
 Aby utworzyć sekwencję zadań wdrażania systemu operacyjnego przy użyciu nośników autonomicznych, skorzystaj z poniższej tabeli przedstawiono wskazówki. Tabela pomaga w określeniu ogólnej sekwencji kroków sekwencji zadań. Pomaga również organizowania i definiowania struktury kroków sekwencji zadań w grupy logiczne. Utworzona sekwencja zadań może się różnić od tego przykładu i może zawierać więcej lub mniej kroków sekwencji zadań, jak i grupy.  

> [!NOTE]  
>  Aby utworzyć nośnika autonomicznego należy zawsze używać Kreatora nośnika sekwencji zadań.  

|Grupa lub krok sekwencji zadań|Opis|  
|---------------------------------|-----------------|  
|Przechwyć pliki i ustawienia — **(Nowa grupa sekwencji zadań)**|Umożliwia utworzenie grupy sekwencji zadań. Grupa sekwencji zadań zawiera podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.|  
|Przechwyć ustawienia systemu Windows|Ten krok sekwencji zadań umożliwia przechwycenie ustawień systemu Windows z komputera docelowego przed ponownym utworzeniem obrazu. Przechwycić nazwę komputera, użytkownika i informacje organizacyjne oraz ustawienia strefy czasowej.|  
|Przechwyć ustawienia sieci|Ten krok sekwencji zadań umożliwia przechwytywanie ustawień sieci z komputera, który odbiera sekwencję zadań. Oprócz ustawień karty sieciowej można przechwycić członkostwo domeny lub grupy roboczej.|  
|Przechwyć pliki użytkownika i ustawienia — **(Nowa podgrupa sekwencji zadań)**|Utwórz grupę sekwencji zadań w innej grupie sekwencji zadań. Ta podgrupa zawiera kroki do przechwycenia danych stanu użytkownika z komputera docelowego przed ponownym utworzeniem obrazu. Podobny do początkowej grupie tego dodany, ta podgrupa przechowuje podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.|  
|Ustaw lokalizację stanu lokalnego|Ten krok sekwencji zadań umożliwia określenie lokalizacji lokalnej za pomocą zmiennej sekwencji zadań ścieżki chronionej. Stan użytkownika jest przechowywany w chronionym katalogu na dysku twardym.|  
|Przechwyć stan użytkownika|Ten krok sekwencji zadań umożliwia przechwytywanie plików użytkownika oraz ustawień, które mają być migrowane do nowego systemu operacyjnego.|  
|Zainstaluj System operacyjny — **(Nowa grupa sekwencji zadań)**|Utwórz inną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do zainstalowania systemu operacyjnego.|  
|Wykonaj ponowny rozruch przy użyciu środowiska Windows PE lub dysku twardego|Ten krok sekwencji zadań umożliwia określenie opcji ponownego uruchomienia komputera, który odbiera sekwencję zadań. Ten krok wyświetla komunikat do użytkownika, że komputer jest ponownie uruchamiany, aby kontynuować instalację.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSInWinPE** . Jeśli skojarzona wartość jest równa **false**, krok sekwencji zadań jest kontynuowany.|  
|Zastosuj system operacyjny|Ten krok sekwencji zadań umożliwia zainstalowanie obrazu systemu operacyjnego na komputerze docelowym. Ten krok powoduje usunięcie wszystkich plików na tym woluminie, z wyjątkiem plików sterowania specyficzne dla programu Configuration Manager. Dotyczy wszystkich obrazów woluminów zawartych w pliku WIM do odpowiednich sekwencyjnych woluminów dysku. Można również określić plik odpowiedzi **Sysprep** w celu skonfigurowania partycji dysku do użycia podczas instalacji.|  
|Zastosuj ustawienia systemu Windows|Ten krok sekwencji zadań umożliwia skonfigurowanie informacji o konfiguracji ustawień systemu Windows dla komputera docelowego. Te ustawienia obejmują użytkownika i informacje organizacyjne, informacji o kluczu produktu lub licencji, strefa czasowa i hasło administratora lokalnego.|  
|Zastosuj ustawienia sieci|Ten krok sekwencji zadań pozwala określić informacje o konfiguracji sieci lub grupy roboczej dla komputera docelowego. Można również określić, czy komputer korzysta z serwera DHCP, lub statycznie przypisać informacje o adresie IP.|  
|Zastosuj pakiet sterowników|Ten krok sekwencji zadań pozwala udostępnić wszystkie sterowniki urządzeń w pakiecie sterowników dostępnym do użycia podczas instalacji systemu Windows. Wszystkie niezbędne sterowniki urządzeń muszą być zawarte na nośniku autonomicznym.|  
|Konfiguracja systemu operacyjnego - **(Nowa grupa sekwencji zadań)**|Utwórz inną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do zainstalowania klienta programu Configuration Manager.|  
|Zainstaluj system Windows i program ConfigMgr|Ten krok sekwencji zadań należy zainstalować oprogramowanie klienta programu Configuration Manager. Configuration Manager instaluje i rejestruje identyfikator GUID klienta programu Configuration Manager. Niezbędne parametry instalacji można przypisać w oknie **Właściwości instalacji** .|  
|Przywróć pliki użytkownika i ustawienia — **(Nowa grupa sekwencji zadań)**|Utwórz inną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do przywrócenia stanu użytkownika.|  
|Przywróć stan użytkownika|Ten krok sekwencji zadań umożliwia zainicjowanie narzędzia migracji stanu użytkowników (USMT). Narzędzie USMT przywraca stan użytkownika i ustawienia, wcześniej przechwycone z krokiem Przechwyć stan użytkownika na komputerze docelowym.|  
