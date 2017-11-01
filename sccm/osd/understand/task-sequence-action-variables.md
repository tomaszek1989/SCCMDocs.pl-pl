---
title: "Zmienne akcji sekwencji zadań"
titleSuffix: Configuration Manager
description: "Zmienne akcji sekwencji, takich jak ustawienia sieci zmiennych, umożliwia określenie ustawień konfiguracyjnych dla jednego kroku w sekwencji zadań programu Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2269031-0977-4f01-a274-420e00630575
caps.latest.revision: "10"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 8c1462ca922f23250ffa44c6433f01a8220d3ad7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="task-sequence-action-variables-in-system-center-configuration-manager"></a>Zmienne akcji sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zmienne akcji sekwencji zadań Określ ustawienia konfiguracji, które są używane przez pojedynczy krok w sekwencji zadań w programie System Center Configuration Manager. Domyślnie ustawienia używane przez krok sekwencji zadań są inicjowane przed uruchomieniem kroku i są dostępne tylko podczas działania skojarzonej sekwencji zadań. Inaczej mówiąc, ustawienie zmiennej sekwencji zadań jest dodawane do środowiska sekwencji zadań przed uruchomieniem kroku sekwencji zadań, a wartość jest usuwana ze środowiska sekwencji zadań po zakończeniu działania przez krok sekwencji zadań.  

## <a name="action-variable-example"></a>Przykład zmiennej akcji  
 Na przykład możesz określić katalog uruchomienia dla akcji wiersza polecenia za pomocą kroku sekwencji zadań **Uruchom wiersz polecenia** . Ten krok obejmuje właściwość **Rozpocznij w** , której domyślna wartość jest przechowywana w środowisku sekwencji zadań jako zmienna **WorkingDirectory** . Zmienna środowiskowa **WorkingDirectory** jest inicjowana przed uruchomieniem akcji sekwencji zadań **Uruchom wiersz polecenia** . Podczas kroku **Uruchom wiersz polecenia** wartość **WorkingDirectory** jest dostępna przez właściwość **Rozpocznij w** . Następnie, po zakończeniu kroku sekwencji zadań, wartość zmiennej **WorkingDirectory** jest usuwana ze środowiska sekwencji zadań. Jeśli sekwencja zawiera inny krok sekwencji zadań **Uruchom wiersz polecenia** , nowa zmienna **WorkingDirectory** zostanie zainicjowana i ustawiona na wartość początkową dla kroku sekwencji zadań.  

 Pomimo że jest dostępna wartość domyślna dla akcji sekwencji zadań, podczas uruchamiania kroku sekwencji zadań można ustawić dowolną nową wartość do użycia przez wiele kroków sekwencji. Jeśli użyjesz jednej z metod tworzenia zmiennej sekwencji zadań do przesłonięcia wbudowanej wartości zmiennej, nowa wartość pozostanie w środowisku i będzie przesłaniać wartość domyślną dla innych kroków sekwencji zadań. W poprzednim przykładzie Jeśli **Ustaw zmienną sekwencji zadań** krok nie zostanie dodany jako pierwszy krok sekwencji zadań i ustawi **WorkingDirectory** zmiennej środowiskowej na wartość **C:\\**, oba **Uruchom wiersz polecenia** kroków sekwencji zadań będzie używać nowej wartości katalogu początkowego.  

## <a name="action-variables-for-task-sequence-actions"></a>Zmienne akcji dla akcji sekwencji zadań  
 Zmienne sekwencji zadań programu Configuration Manager są pogrupowane według ich skojarzonych akcji sekwencji zadań. Użyj następujących linków, aby zebrać informacje dotyczące zmiennych akcji skojarzonych z konkretną akcją. Zmienne sekwencji zadania określają sposób realizacji akcji sekwencji zadania. Akcja sekwencji zadania odczytuje i używa zmiennych oznaczonych przez użytkownika jako zmienne wejściowe. Do ustawienia zmiennych w czasie wykonywania można też użyć akcji Set Task Sequence Variable lub obiektu TSEnvironment COM. Tylko akcja sekwencji zadania oznacza zmienne jako zmienne wyjściowe, które są odczytywane przez akcje występujące później w sekwencji zadania.  

> [!NOTE]  
>  Nie wszystkie akcje sekwencji zadań są skojarzone ze zbiorem zmiennych sekwencji zadań. Na przykład mimo że istnieją zmienne skojarzone z akcją Włącz funkcję BitLocker, nie ma zmiennych skojarzonych z akcją Wyłącz funkcję BitLocker.  

###  <a name="BKMK_ApplyDataImage"></a> Zmienne akcji sekwencji zadań Zastosuj obraz danych  
 Zmienne tej akcji określają, który obraz w pliku WIM jest stosowany dla komputera docelowego i czy pliki na partycji docelowej mają zostać usunięte. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [zastosować kroku sekwencji zadań obraz danych](task-sequence-steps.md#BKMK_ApplyDataImage).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDDataImageIndex<br /><br /> (dane wejściowe)|Określa wartość indeksu obrazu, który zostanie zastosowany dla komputera docelowego.|  
|OSDWipeDestinationPartition<br /><br /> (dane wejściowe)|Określa, czy pliki znajdujące się na partycji docelowej zostaną usunięte.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  

###  <a name="BKMK_ApplyDriverPackage"></a> Zmienne akcji sekwencji zadań Zastosuj pakiet sterownika  
 Zmienne tej akcji określają informacje na potrzeby instalacji sterowników pamięci masowej oraz czy niepodpisane sterowniki maja być instalowane. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [zastosuj pakiet sterowników](task-sequence-steps.md#BKMK_ApplyDriverPackage).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDApplyDriverBootCriticalContentUniqueID<br /><br /> (dane wejściowe)|Określa identyfikator zawartości sterownika urządzenia pamięci masowej do zainstalowania z pakietu sterowników. Jeśli ta zmienna nie zostanie określona, żaden sterownik pamięci masowej nie zostanie zainstalowany.|  
|OSDApplyDriverBootCriticalINFFile<br /><br /> (dane wejściowe)|Określa plik INF sterownika pamięci masowej do zainstalowania.<br /><br /> <br /><br /> Ta zmienna sekwencji zadań jest wymagana, jeśli ustawiono zmienną OSDApplyDriverBootCriticalContentUniqueID.|  
|OSDApplyDriverBootCriticalHardwareComponent<br /><br /> (dane wejściowe)|Określa, czy jest zainstalowany sterownik urządzenia pamięci masowej, musi to być **scsi**.<br /><br /> <br /><br /> Ta zmienna sekwencji zadań jest wymagana, jeśli ustawiono zmienną OSDApplyDriverBootCriticalContentUniqueID.|  
|OSDApplyDriverBootCriticalID<br /><br /> (dane wejściowe)|Określa identyfikator o krytycznym znaczeniu dla rozruchu dla sterownika urządzenia pamięci masowej do zainstalowania. Ten identyfikator jest wymieniony w "**scsi**" pliku txtsetup.oem sterownika urządzenia.<br /><br /> <br /><br /> Ta zmienna sekwencji zadań jest wymagana, jeśli ustawiono zmienną OSDApplyDriverBootCriticalContentUniqueID.|  
|OSDAllowUnsignedDriver<br /><br /> (dane wejściowe)|Określa, czy system Windows ma zezwalać na instalowanie niepodpisanych sterowników urządzeń. Ta zmienna sekwencji zadań nie jest używana podczas wdrażania systemu Windows Vista i nowszych systemów operacyjnych.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  

###  <a name="BKMK_ApplyNetworkSettings"></a> Zmienne akcji sekwencji zadań Zastosuj ustawienia sieci  
 Zmienne tej akcji określają ustawienia sieci dla komputera docelowego, takie jak ustawienia kart sieciowych komputera, domeny i grupy roboczej. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [zastosować krok ustawienia sieci](task-sequence-steps.md#BKMK_ApplyNetworkSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDAdapter<br /><br /> (dane wejściowe)|Ta zmienna sekwencji zadań jest zmienną tablicową. Każdy element tablicy reprezentuje ustawienia jednej karty sieciowej w komputerze. Ustawienia zdefiniowane dla każdej karty są dostępne przez połączenie nazwy zmiennej tablicowej z indeksem karty sieciowej liczonym od 0 i nazwą właściwości.<br /><br /> <br /><br /> Jeśli za pomocą tej akcji sekwencji zadań zostanie skonfigurowanych wiele kart sieciowych, właściwości drugiej karty sieciowej są zdefiniowane przy użyciu jej indeksu w nazwie zmiennej, na przykład OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList, OSDAdapter1DNSDomain, OSDAdapter1WINSServerList, OSDAdapter1EnableWINS i tak dalej.<br /><br /> <br /><br /> Na przykład następujące nazwy zmiennych mogą służyć do zdefiniowania właściwości pierwszej karty sieciowej, która zostanie skonfigurowana przez tę akcję sekwencji zadań:<br /><br /> <ul><li>**OSDAdapter0EnableDHCP** — wartość TRUE powoduje włączenie protokołu dynamicznej konfiguracji hosta (DHCP) dla karty.<br />    To ustawienie jest wymagane. Możliwe wartości to:  Wartość TRUE lub False.</li><li>**OSDAdapter0IPAddressList** — rozdzielana przecinkami lista adresów IP dla karty. Ta właściwość jest ignorowana, chyba że właściwość **EnableDHCP** jest ustawiona na wartość **false**.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0SubnetMask** — rozdzielana przecinkami lista masek podsieci. Ta właściwość jest ignorowana, chyba że właściwość **EnableDHCP** jest ustawiona na wartość **false**.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0Gateways** — rozdzielana przecinkami lista adresów IP bramy. Ta właściwość jest ignorowana, chyba że właściwość **EnableDHCP** jest ustawiona na wartość **false**.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0DNSDomain** — domena systemu nazw domen (DNS) dla karty.</li><li>**OSDAdapter0DNSServerList** — rozdzielana przecinkami lista serwerów DNS dla karty.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0EnableDNSRegistration** - **true** powoduje zarejestrowanie adresu IP karty w systemie DNS.</li><li>**OSDAdapter0EnableFullDNSRegistration** - **true** można zarejestrować adresu IP karty w usłudze DNS pod pełną nazwą DNS dla komputera.</li><li>**OSDAdapter0EnableIPProtocolFiltering** - **true** umożliwiające filtrowania protokołu IP na karcie.</li><li>**OSDAdapter0IPProtocolFilterList** — rozdzielana przecinkami lista protokołów, które mogą być uruchamiane przy użyciu protokołu IP. Ta właściwość jest ignorowana, jeśli właściwość **EnableIPProtocolFiltering** jest ustawiona na wartość **false**.</li><li>**OSDAdapter0EnableTCPFiltering** - **true** Aby włączyć port TCP filtrowania dla karty.</li><li>**OSDAdapter0TCPFilterPortList** — rozdzielana przecinkami lista portów, które mogą mieć uprawnienia dostępu dla protokołu TCP. Ta właściwość jest ignorowana, jeśli właściwość **EnableTCPFiltering** jest ustawiona na wartość **false**.</li><li>**OSDAdapter0TcpipNetbiosOptions** — opcje systemu NetBIOS przez TCP/IP. Dopuszczalne są następujące wartości:<br /><br /> <ul><li>0 Ustawienie systemu NetBIOS z serwera DHCP.</li><li>1 Włącz system NetBIOS przez TCP/IP.</li><li>2 Wyłącz system NetBIOS przez TCP/IP.</li></ul></li><li>**OSDAdapter0EnableWINS** - **true** do korzystania z usługi WINS do rozpoznawania nazw.</li><li>**OSDAdapter0WINSServerList** — rozdzielana przecinkami lista adresów IP serwerów WINS. Ta właściwość jest ignorowana, chyba że właściwość **EnableWINS** jest ustawiona na wartość **true**.</li><li>**OSDAdapter0MacAddress** -Media access adres kontrolera (MAC) używany do dopasowania ustawień do fizycznej karty sieciowej.</li><li>**OSDAdapter0Name** — nazwa połączenia sieciowego w postaci, w jakiej jest wyświetlana w program Panelu sterowania połączeń sieciowych. Nazwa ma od 0 do 255 znaków długości.</li><li>**OSDAdapter0Index** — indeks ustawień karty sieciowej w tablicy ustawień.<br /><br />     OSDAdapterCount = 1<br />    OSDAdapter0EnableDHCP = FALSE<br />    OSDAdapter0IPAddressList = 192.168.0.40<br />    OSDAdapter0SubnetMask = 255.255.255.0<br />    OSDAdapter0Gateways = 192.168.0.1<br />    OSDAdapter0DNSSuffix=contoso.com</li></ul>|  
|OSDAdapterCount<br /><br /> (dane wejściowe)|Określa liczbę kart sieciowych zainstalowanych w komputerze docelowym. Jeśli wartość **OSDAdapterCount** jest ustawiona, wszystkie opcje konfiguracji każdego adaptera muszą być ustawione. Na przykład jeśli ustawisz wartość **OSDAdapterTCPIPNetbiosOptions** dla określonej karty, to wszystkie wartości dla tej karty muszą również zostać skonfigurowane.<br /><br /> <br /><br /> Jeśli ta wartość nie jest określona, wszystkie wartości **OSDAdapter** są ignorowane.|  
|OSDDNSDomain<br /><br /> (dane wejściowe)|Określa podstawowy serwer DNS, który jest używany przez komputer docelowy.|  
|OSDDomainName<br /><br /> (dane wejściowe)|Określa nazwę domeny systemu Windows, do której jest przyłączany komputer docelowy. Określona wartość musi być prawidłową nazwą domeny usług domenowych Active Directory.|  
|OSDDomainOUName<br /><br /> (dane wejściowe)|Określa nazwę jednostki organizacyjnej (OU), do której jest przyłączany komputer docelowy, w formacie RFC 1779. Jeśli wartość jest określona, musi zawierać pełną ścieżkę.<br /><br /> Przykład:<br /><br /> **LDAP://OU=MojaJO,DC=MojaDomena,DC=MojaFirma,DC=com**|  
|OSDEnableTCPIPFiltering<br /><br /> (dane wejściowe)|Określa, czy filtrowanie protokołu TCP/IP jest włączone.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDJoinAccount<br /><br /> (dane wejściowe)|Określa konto sieciowe, które służy do dodawania komputera docelowego do domeny systemu Windows.|  
|OSDJoinPassword<br /><br /> (dane wejściowe)|Określa hasło dostępu do sieci, które służy do dodawania komputera docelowego do domeny systemu Windows.|  
|OSDNetworkJoinType<br /><br /> (dane wejściowe)|Określa, czy komputer docelowy jest przyłączany do domeny systemu Windows lub grupy roboczej.<br /><br /> Wartość**„0”** wskazuje, że komputer docelowy zostanie przyłączony do domeny systemu Windows. Wartość**„1”** określa, że komputer zostanie przyłączony do grupy roboczej.<br /><br /> Prawidłowe wartości:<br /><br /> **„0”**<br /><br /> **„1”**|  
|OSDDNSSuffixSearchOrder<br /><br /> (dane wejściowe)|Określa kolejność wyszukiwania w usłudze DNS dla komputera docelowego.|  
|OSDWorkgroupName<br /><br /> (dane wejściowe)|Określa nazwę grupy roboczej, do której jest przyłączany komputer docelowy.<br /><br /> Musisz określić albo tę wartość, albo wartość **OSDDomainName** . Nazwa grupy roboczej może mieć maksymalnie 32 znaki.<br /><br /> Przykład:<br /><br /> **„Księgowość”**|  

###  <a name="BKMK_ApplyOperatingSystem"></a> Zmienne akcji sekwencji zadań Zastosuj obraz systemu operacyjnego  
 Zmienne tej akcji określają ustawienia dla systemu operacyjnego, który ma zostać zainstalowany na komputerze docelowym. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Zastosuj obraz systemu operacyjnego](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDConfigFileName<br /><br /> (dane wejściowe)|Określa nazwę pliku odpowiedzi wdrożenia systemu operacyjnego skojarzonego z pakietem wdrożenia systemu operacyjnego.|  
|OSDImageIndex<br /><br /> (dane wejściowe)|Określa wartość indeksu obrazu w pliku WIM, który zostanie zastosowany dla komputera docelowego.|  
|OSDInstallEditionIndex<br /><br /> (dane wejściowe)|Określa wersję systemu operacyjnego Windows Vista lub nowszego, który jest instalowany. Jeśli wersja nie jest określona, Instalator systemu Windows określi wersję do zainstalowania przy użyciu przywołanego klucza produktu.<br /><br /> Użyj wartości zero (0), tylko jeśli są spełnione następujące warunki:<br /><br /> -Instalowany jest systemem operacyjnym starszym niż Windows Vista<br />— W przypadku instalowania wersji używającej licencji zbiorczej systemu Windows Vista lub nowszy, a klucz produktu nie jest określony.<br /><br /> Prawidłowe wartości:<br /><br /> **„0”** (domyślnie)|  
|OSDTargetSystemDrive (dane wyjściowe)|Określa literę dysku partycji zawierającej pliki systemu operacyjnego.|  

###  <a name="BKMK_ApplyWindowsSettings"></a> Zmienne akcji sekwencji zadań Zastosuj ustawienia systemu Windows  
 Zmienne tej akcji określają ustawienia systemu Windows dla komputera docelowego, na przykład nazwę komputera, klucz produktu systemu Windows, zarejestrowanego użytkownika i organizację oraz hasło administratora lokalnego. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Zastosuj ustawienia systemu Windows](task-sequence-steps.md#BKMK_ApplyWindowsSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDComputerName<br /><br /> (dane wejściowe)|Określa nazwę komputera docelowego.<br /><br /> Przykład:<br /><br /> **„%_SMSTSMachineName%”** (domyślnie)|  
|OSDProductKey<br /><br /> (dane wejściowe)|Określa klucz produktu systemu Windows. Określona wartość musi mieć od 1 do 255 znaków.|  
|OSDRegisteredUserName<br /><br /> (dane wejściowe)|Określa domyślną nazwę zarejestrowanego użytkownika w nowym systemie operacyjnym. Określona wartość musi mieć od 1 do 255 znaków.|  
|OSDRegisteredOrgName<br /><br /> (dane wejściowe)|Określa domyślną nazwę zarejestrowanej organizacji w nowym systemie operacyjnym. Określona wartość musi mieć od 1 do 255 znaków.|  
|OSDTimeZone<br /><br /> (dane wejściowe)|Określa domyślne ustawienie strefy czasowej używane w nowym systemie operacyjnym.|  
|OSDServerLicenseMode<br /><br /> (dane wejściowe)|Określa używany tryb licencji systemu Windows Server.<br /><br /> Prawidłowe wartości:<br /><br /> **„PerSeat”**<br /><br /> **„PerServer”**|  
|OSDServerLicenseConnectionLimit<br /><br /> (dane wejściowe)|Określa maksymalną dozwoloną liczbę połączeń. Określona liczba musi być w zakresie od 5 do 9999 połączeń.|  
|OSDRandomAdminPassword<br /><br /> (dane wejściowe)|Określa losowo wygenerowane hasło dla konta administratora w nowym systemie operacyjnym. Jeśli ustawiono **true**, konto administratora lokalnego zostanie wyłączone na komputerze docelowym. Jeśli ustawiono **false**, konto administratora lokalnego zostanie włączona na komputerze docelowym i hasło konta administratora lokalnego zostanie przypisana wartość zmiennej **OSDLocalAdminPassword**.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  
|OSDLocalAdminPassword<br /><br /> (dane wejściowe)|Określa hasło administratora lokalnego. Ta wartość jest ignorowana, jeśli opcja **Losowo generuj hasło administratora lokalnego i wyłącz konto na wszystkich obsługiwanych platformach** jest włączona. Określona wartość musi mieć od 1 do 255 znaków.|  

###  <a name="BKMK_AutoApplyDrivers"></a> Zmienne akcji sekwencji zadań Automatycznie zastosuj sterowniki  
 Zmienne tej akcji określają, które sterowniki systemu Windows są instalowane na komputerze docelowym i czy są instalowane niepodpisane sterowniki. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [automatycznie Zastosuj sterowniki](task-sequence-steps.md#BKMK_AutoApplyDrivers).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDAutoApplyDriverCategoryList<br /><br /> (dane wejściowe)|Rozdzielana przecinkami lista unikatowych identyfikatorów kategorii katalogu sterownika. Jeśli wartość jest określona, akcja sekwencji zadań **Automatycznie zastosuj sterowniki** uwzględnia podczas instalowania sterowników tylko te, które należą do co najmniej jednej z podanych kategorii. Ta wartość jest opcjonalna i domyślnie nie jest ustawiona. Dostępne identyfikatory kategorii można uzyskać, wyliczając listę obiektów **SMS_CategoryInstance** w lokacji.|  
|OSDAllowUnsignedDriver<br /><br /> (dane wejściowe)|Określa, czy konfiguracja systemu Windows zezwala na instalowanie niepodpisanych sterowników urządzeń. Ta zmienna sekwencji zadań nie jest używana podczas wdrażania systemu operacyjnego Windows Vista i nowszych.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDAutoApplyDriverBestMatch<br /><br /> (dane wejściowe)|Określa działanie wykonywane przez akcję sekwencji zadań, jeśli w katalogu sterowników znajduje się wiele sterowników urządzenia, które są zgodne z urządzeniem sprzętowym. Jeśli ustawiono **"true"**, zostanie zainstalowany tylko najlepszy sterownik urządzenia.  Jeśli **false**, zostaną zainstalowane wszystkie zgodne sterowniki urządzenia, a system operacyjny wybierze najlepszy sterownik do użycia.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  

###  <a name="BKMK_CaptureNetworkSettings"></a> Zmienne akcji sekwencji zadań Przechwyć ustawienia sieci  
 Zmienne tej akcji określają, czy informacje o konfiguracji ustawień karty sieciowej (TCP/IP, DNS i WINS) są przechwytywane oraz czy informacje o przynależności do grupy roboczej lub domeny są migrowane w ramach wdrożenia systemu operacyjnego. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Przechwyć ustawienia sieci](task-sequence-steps.md#BKMK_CaptureNetworkSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDMigrateAdapterSettings<br /><br /> (dane wejściowe)|Określa, czy informacje o konfiguracji ustawień karty sieciowej (TCP/IP, DNS i WINS) są przechwytywane.<br /><br /> Przykłady:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  
|OSDMigrateNetworkMembership<br /><br /> (dane wejściowe)|Określa, czy informacje o przynależności do grupy roboczej lub domeny są migrowane w ramach wdrożenia systemu operacyjnego.<br /><br /> Przykłady:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  

###  <a name="BKMK_CaptureOperatingSystemImage"></a> Zmienne akcji sekwencji zadań Przechwyć obraz systemu operacyjnego  
 Zmienne tej akcji określają informacje o przechwytywanym obrazie systemu operacyjnego, takie jak miejsce przechowywania obrazu, jego twórcę i opis. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Przechwyć obraz systemu operacyjnego](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDCaptureAccount<br /><br /> (dane wejściowe)|Określa nazwę konta systemu Windows, które ma uprawnienia do przechowywania przechwyconego obrazu w udziale sieciowym.|  
|OSDCaptureAccountPassword<br /><br /> (dane wejściowe)|Określa hasło konta systemu Windows używanego do przechowywania przechwyconego obrazu w udziale sieciowym.|  
|OSDCaptureDestination<br /><br /> (dane wejściowe)|Określa lokalizację, w której jest zapisywany przechwycony obraz systemu operacyjnego. Maksymalna długość nazwy katalogu to 255 znaków.|  
|OSDImageCreator<br /><br /> (dane wejściowe)|Opcjonalna nazwa użytkownika, który utworzył obraz. Ta nazwa jest zapisana w pliku WIM. Maksymalna długość nazwy użytkownika to 255 znaków.|  
|OSDImageDescription<br /><br /> (dane wejściowe)|Opcjonalny opis zdefiniowany przez użytkownika dla przechwyconego obrazu systemu operacyjnego. Ten opis jest zapisany w pliku WIM. Maksymalna długość opisu to 255 znaków.|  
|OSDImageVersion<br /><br /> (dane wejściowe)|Opcjonalny numer wersji zdefiniowany przez użytkownika, który ma zostać przypisany do przechwyconego obrazu systemu operacyjnego. Numer wersji jest zapisany w pliku WIM. Ta wartość może być dowolną kombinacją liter o maksymalnej długości 32 znaków.|  
|OSDTargetSystemRoot<br /><br /> (dane wejściowe)|Określa ścieżkę do katalogu zainstalowanego systemu operacyjnego Windows na komputerze odniesienia. Ten system operacyjny jest weryfikowany jako możliwy do przechwycenia obsługiwanego systemu operacyjnego przez program Configuration Manager.|  

###  <a name="BKMK_CaptureUserState"></a> Zmienne akcji sekwencji zadań Przechwyć stan użytkownika  
 Zmienne tej akcji określają informacje używane przez narzędzie do migracji stanu użytkowników (USMT), takie jak folder, w którym jest zapisany stan użytkownika, opcje wiersza polecenia narzędzia USMT i pliki konfiguracji używane do kontrolowania przechwytywania profilów użytkowników.  Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Przechwyć stan użytkownika](task-sequence-steps.md#BKMK_CaptureUserState).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (dane wejściowe)|Nazwa ścieżki UNC lub ścieżki lokalnej folderu, w którym jest zapisany stan użytkownika. Brak wartości domyślnej.|  
|OSDMigrateAdditionalCaptureOptions<br /><br /> (dane wejściowe)|Określa opcje migracji stanu użytkowników (USMT) Narzędzie wiersza polecenia, które są używane podczas przechwytywania stanu użytkownika, ale nie są widoczne w interfejsie użytkownika programu Configuration Manager. Dodatkowe opcje są określone w postaci ciągu, który jest dołączany do automatycznie wygenerowanego wiersza polecenia narzędzia USMT.<br /><br /> <br /><br /> Opcje narzędzia USMT określone za pomocą tej zmiennej sekwencji zadań nie są weryfikowane pod kątem dokładności przed uruchomieniem sekwencji zadań.|  
|OSDMigrateMode<br /><br /> (dane wejściowe)|Umożliwia dostosowanie plików przechwytywanych przez narzędzie USMT. Jeśli ta zmienna jest ustawiona na "Prosty", są używane tylko standardowe pliki konfiguracji narzędzia USMT. Jeśli ta zmienna jest ustawiona na wartość "Zaawansowany", następnie zmienną sekwencji zadań OSDMigrateConfigFiles Określa pliki konfiguracji używane przez narzędzie USMT.<br /><br /> Prawidłowe wartości:<br /><br /> **„Simple”**<br /><br /> **„Advanced”**|  
|OSDMigrateConfigFiles<br /><br /> (dane wejściowe)|Określa pliki konfiguracji służące do kontrolowania przechwytywania profilów użytkowników. Ta zmienna jest używana tylko wtedy, gdy zmienna OSDMigrateMode jest ustawiona na wartość "Zaawansowany". Ta wartość określająca rozdzielaną przecinkami listę jest ustawiana na potrzeby wykonania niestandardowej migracji profilu użytkownika.<br /><br /> Przykład: miguser.xml,migsys.xml,migapps.xml|  
|OSDMigrateContinueOnLockedFiles<br /><br /> (dane wejściowe)|Umożliwia kontynuowanie przechwytywania stanu użytkownika, jeśli nie można przechwycić niektórych plików.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (dane wejściowe)|Włącza pełne rejestrowanie dla narzędzia USMT.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDMigrateSkipEncryptedFiles<br /><br /> (dane wejściowe)|Określa, czy zaszyfrowane pliki są przechwytywane.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|_OSDMigrateUsmtPackageID<br /><br /> (dane wejściowe)|Określa identyfikator pakietu pakietu programu Configuration Manager, który będzie zawierać pliki narzędzia USMT. Ta zmienna jest wymagana.|  

###  <a name="BKMK_CaptureWindowsSettings"></a> Zmienne akcji sekwencji zadań Przechwyć ustawienia systemu Windows  
 Zmienne tej akcji określają, czy konkretne ustawienia systemu Windows są migrowane do komputera docelowego (np. nazwa komputera, nazwa zarejestrowanej organizacji i informacje o strefie czasowej). Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Przechwyć ustawienia systemu Windows](task-sequence-steps.md#BKMK_CaptureWindowsSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDMigrateComputerName<br /><br /> (dane wejściowe)|Określa, czy nazwa komputera jest migrowana.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**<br /><br /> Jeśli ma wartość "true", zmienna OSDComputerName jest ustawiona na nazwę NetBIOS komputera.|  
|OSDComputerName<br /><br /> (dane wyjściowe)|Ustawiona na nazwę NetBIOS komputera. Wartość jest ustawiona tylko wtedy, gdy zmienna OSDMigrateComputerName jest ustawiona na wartość "true".|  
|OSDMigrateRegistrationInfo<br /><br /> (dane wejściowe)|Określa, czy informacje o użytkowniku komputera i organizacyjne są migrowane.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**<br /><br /> Jeśli wartość to "true", zmienna OSDRegisteredOrgName jest ustawiona na nazwę zarejestrowanej organizacji komputera.|  
|OSDRegisteredOrgName<br /><br /> (dane wyjściowe)|Ustawiona na nazwę zarejestrowanej organizacji komputera. Wartość jest ustawiona tylko wtedy, gdy zmienna OSDMigrateRegistrationInfo jest ustawiona na wartość "true".|  
|OSDMigrateTimeZone<br /><br /> (dane wejściowe)|Określa, czy strefa czasowa komputera jest migrowana.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**<br /><br /> Jeśli wartość to "true", następnie zmienna OSDTimeZone ustawiono na strefę czasową komputera.|  
|OSDTimeZone<br /><br /> (dane wyjściowe)|Ustawiona na strefę czasową komputera. Wartość jest ustawiona tylko wtedy, gdy zmienna OSDMigrateTimeZone jest ustawiona na wartość "true".|  

###  <a name="BKMK_ConnecttoNetworkFolder"></a> Zmienne akcji sekwencji zadań Połącz z folderem sieciowym  
 Zmienne tej akcji określają informacje o folderze w sieci, takie jak konto i hasło używane do nawiązania połączenia z folderem sieciowym, litera dysku folderu i ścieżka do folderu. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [połączenia do folderu sieciowego](task-sequence-steps.md#BKMK_ConnectToNetworkFolder).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|SMSConnectNetworkFolderAccount<br /><br /> (dane wejściowe)|Określa konto administratora używane do nawiązania połączenia z udziałem sieciowym.|  
|SMSConnectNetworkFolderDriveLetter<br /><br /> (dane wejściowe)|Określa literę dysku sieciowego, z którym ma zostać nawiązane połączenie. Ta wartość jest opcjonalna. Jeśli nie zostanie określona, połączenie sieciowe nie zostanie zamapowane na literę dysku. Jeśli ta wartość jest określona, to musi należeć do zakresu od D: do Z:.  Ponadto nie należy używać wartości X:, ponieważ jest to litera dysku używana przez środowisko Windows PE w fazie Windows PE.<br /><br /> Przykłady:<br /><br /> **„D:”**<br /><br /> **„E:”**|  
|SMSConnectNetworkFolderPassword<br /><br /> (dane wejściowe)|Określa hasło dostępu do sieci używane do nawiązania połączenia z udziałem sieciowym.|  
|SMSConnectNetworkFolderPath<br /><br /> (dane wejściowe)|Określa ścieżkę sieciową dla połączenia.<br /><br /> Przykład:<br /><br /> **"\\\servername\sharename"**|  

###  <a name="BKMK_EnableBitLocker"></a> Zmienne akcji sekwencji zadań Włącz funkcję BitLocker  
 Zmienne tej akcji określają opcje odzyskiwania hasła i klucza uruchomienia używane do włączenia funkcji BitLocker na komputerze docelowym. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Włącz funkcję BitLocker](task-sequence-steps.md#BKMK_EnableBitLocker).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDBitLockerRecoveryPassword<br /><br /> (dane wejściowe)|Zamiast generowania losowego hasła odzyskiwania akcja sekwencji zadań **Włącz funkcję BitLocker** używa określonej wartości jako hasła odzyskiwania. Wartość musi być prawidłowym liczbowym hasłem odzyskiwania funkcji BitLocker.|  
|OSDBitLockerStartupKey<br /><br /> (dane wejściowe)|Zamiast generowania losowego klucza uruchomienia dla opcji zarządzania kluczami **klucz uruchomienia tylko na USB** **Włącz funkcję BitLocker** akcji sekwencji zadań używa modułu (TPM) jako klucza uruchomienia. Wartość musi być prawidłowym 256-bitowym kluczem uruchomienia funkcji BitLocker zakodowanym w formacie Base64.|  

###  <a name="BKMK_FormatPartitionDisk"></a> Zmienne akcji sekwencji zadań Formatuj dysk i podziel go na partycje  
 Zmienne tej akcji określają informacje dotyczące formatowania i partycjonowania dysku fizycznego, takie jak numer dysku i tablica ustawień partycji. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Format i partycji](task-sequence-steps.md#BKMK_FormatandPartitionDisk).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDDiskIndex<br /><br /> (dane wejściowe)|Określa numer dysku fizycznego do podzielenia na partycje.|  
|OSDDiskpartBiosCompatibilityMode<br /><br /> (dane wejściowe)|Określa, czy wyłączyć optymalizacje wyrównania pamięci podręcznej podczas partycjonowania dysku twardego w celu zapewnienia zgodności z pewnymi typami systemu BIOS. Może to być konieczne w przypadku wdrażania systemów operacyjnych Windows XP lub Windows Server 2003. Aby uzyskać więcej informacji, zobacz [artykuł 931760](http://go.microsoft.com/fwlink/?LinkId=134081) i [artykuł 931761](http://go.microsoft.com/fwlink/?LinkId=134082) w bazie wiedzy Microsoft Knowledge Base.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDGPTBootDisk<br /><br /> (dane wejściowe)|Określa, czy utworzyć partycję EFI na dysku twardym GPT, dzięki czemu będzie można go użyć jako dysku startowego w komputerach z systemem EFI.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDPartitions<br /><br /> (dane wejściowe)|Określa tablicę ustawień partycji. Informacje na temat uzyskiwania dostępu do zmiennych tablicowych w środowisku sekwencji zadań zawiera temat dotyczący zestawu SDK.<br /><br /> Ta zmienna sekwencji zadań jest zmienną tablicową. Każdy element tablicy reprezentuje ustawienia jednej partycji na dysku twardym. Ustawienia zdefiniowane dla każdej partycji są dostępne przez połączenie nazwy zmiennej tablicowej z numerem partycji dysku liczonym od 0 i nazwą właściwości.<br /><br /> Na przykład następujące nazwy zmiennych mogą służyć do zdefiniowania właściwości pierwszej partycji, która zostanie utworzona przez tę akcję sekwencji zadań na dysku twardym:<br /><br /> - **OSDPartitions0Type** — Określa typ partycji. Ta właściwość jest wymagana. Prawidłowe wartości to „**Primary**”, „**Extended**”, „**Logical**” i „**Hidden**”.<br />-   **OSDPartitions0FileSystem** — określa typ systemu plików do użycia podczas formatowania partycji. Jest to opcjonalna właściwość. Jeśli system plików nie zostanie określony, partycja nie zostanie sformatowana. Prawidłowe wartości to „**FAT32**” i „**NTFS**”.<br />-   **OSDPartitions0Bootable** — określa, czy partycja jest partycją rozruchową. Ta właściwość jest wymagana. Jeśli ta wartość jest równa „**TRUE**” w przypadku dysków MBR, partycja zostanie ustawiona jako aktywna.<br />-   **OSDPartitions0QuickFormat** — określa typ użytego formatu. Ta właściwość jest wymagana. Jeśli ta wartość jest równa „**TRUE**”, zostanie wykonane szybkie formatowanie. W przeciwnym razie zostanie wykonane pełne formatowanie.<br />-   **OSDPartitions0VolumeName** — określa nazwę przypisywaną do woluminu, gdy jest on formatowany. Jest to właściwość opcjonalna.<br />-   **OSDPartitions0Size** — określa rozmiar partycji. Jednostki są określone przez zmienną **OSDPartitions0SizeUnits** . Jest to właściwość opcjonalna. Jeśli ta właściwość nie jest określona, utworzona partycja będzie zajmowała całe wolne miejsce.<br />-   **OSDPartitions0SizeUnits** — określa jednostki, które będą używane przy interpretowaniu zmiennej sekwencji zadań **OSDPartitions0Size** . Jest to właściwość opcjonalna. Prawidłowe wartości to „**MB**” (domyślnie), „**GB**” i „**Percent**”.<br />-   **OSDPartitions0VolumeLetterVariable** — partycje będą zawsze używać kolejnej dostępnej litery dysku w środowisku Windows PE po utworzeniu. Użyj tej opcjonalnej właściwości do określenia nazwy innej zmiennej sekwencji zadań, która zostanie użyta do zapisania litery nowego dysku do użycia w przyszłości.<br /><br /> <br /><br /> Jeśli akcja sekwencji zadań definiuje wiele partycji, właściwości drugiej partycji można zdefiniować przy użyciu jej indeksu w nazwie zmiennej, na przykład **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat**, **OSDPartitions1VolumeName** i tak dalej.|  
|OSDPartitionStyle<br /><br /> (dane wejściowe)|Określa styl partycji do użycia podczas tworzenia partycji na dysku. Wartość „**MBR**” oznacza styl partycji głównego rekordu rozruchowego, a wartość „**GPT**” oznacza styl tabeli partycji GUID.<br /><br /> Prawidłowe wartości:<br /><br /> **„GPT”**<br /><br /> **„MBR”**|  

###  <a name="BKMK_InstallSoftwareUpdates"></a> Zmienne akcji sekwencji zadań Zainstaluj aktualizacje oprogramowania  
 Zmienna tej akcji określa, czy zainstalować wszystkie aktualizacje, czy tylko aktualizacje obowiązkowe. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Zainstaluj aktualizacje oprogramowania](task-sequence-steps.md#BKMK_InstallSoftwareUpdates).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|SMSInstallUpdateTarget<br /><br /> (dane wejściowe)|Określa, czy zainstalować wszystkie aktualizacje, czy tylko aktualizacje obowiązkowe.<br /><br /> Prawidłowe wartości:<br /><br /> **„All”**<br /><br /> **„Mandatory”**|  

###  <a name="BKMK_JoinDomainWorkgroup"></a> Zmienne akcji sekwencji zadań Przyłącz do domeny lub grupy roboczej  
 Zmienne tej akcji określają informacje niezbędne do przyłączenia komputera docelowego do domeny systemu Windows lub grupy roboczej. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Przyłącz do domeny lub grupy roboczej](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDJoinAccount<br /><br /> (dane wejściowe)|Określa konto, które służy do przyłączania komputera docelowego do domeny systemu Windows. Ta zmienna jest wymagana w przypadku przyłączania do domeny.|  
|OSDJoinDomainName<br /><br /> (dane wejściowe)|Określa nazwę domeny systemu Windows, do której jest przyłączany komputer docelowy. Długość nazwy domeny systemu Windows musi wynosić od 1 do 255 znaków.|  
|OSDJoinDomainOUName<br /><br /> (dane wejściowe)|Określa nazwę jednostki organizacyjnej (OU), do której jest przyłączany komputer docelowy, w formacie RFC 1779. Jeśli wartość jest określona, musi zawierać pełną ścieżkę. Długość nazwy jednostki organizacyjnej domeny systemu Windows musi wynosić od 0 do 32 767 znaków. Ta wartość nie jest ustawiona, jeśli zmienna **OSDJoinType** jest ustawiona na wartość „1” (przyłączenie do grupy roboczej).<br /><br /> Przykład:<br /><br /> **LDAP://OU=MojaJO,DC=MojaDomena,DC=MojaFirma,DC=com**|  
|OSDJoinPassword<br /><br /> (dane wejściowe)|Określa hasło dostępu do sieci, które jest używane przez komputer docelowy na potrzeby przyłączenia do domeny systemu Windows. Jeśli zmienna nie zostanie określona, zostanie podjęta próba przy użyciu pustego hasła. Ta wartość jest wymagana, jeśli zmienna **OSDJoinType** jest ustawiona na wartość „**0**” (przyłączenie do domeny).|  
|OSDJoinSkipReboot<br /><br /> (dane wejściowe)|Określa, czy pominąć ponowne uruchomienie po przyłączeniu komputera docelowego do domeny lub grupy roboczej.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”**|  
|OSDJoinType<br /><br /> (dane wejściowe)|Określa, czy komputer docelowy jest przyłączany do domeny systemu Windows lub grupy roboczej. Aby przyłączyć komputer docelowy do domeny systemu Windows, określ wartość „**0**”. Aby przyłączyć komputer docelowy do grupy roboczej, określ wartość „**1**”.<br /><br /> Prawidłowe wartości:<br /><br /> **„0”**<br /><br /> **„1”**|  
|OSDJoinWorkgroupName<br /><br /> (dane wejściowe)|Określa nazwę grupy roboczej, do której zostanie przyłączony komputer docelowy. Długość nazwy grupy roboczej musi wynosić od 1 do 32 znaków.<br /><br /> Przykład:<br /><br /> **„Księgowość”**|  

###  <a name="BKMK_PrepareWindowsCapture"></a> Zmienne akcji sekwencji zadań Przygotuj system Windows do przechwytywania  
 Zmienne tej akcji określają informacje używane do przechwycenia systemu operacyjnego Windows z komputera docelowego. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [przygotować klienta programu ConfigMgr do przechwycenia](task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDBuildStorageDriverList<br /><br /> (dane wejściowe)|Określa, czy program sysprep tworzy listę sterowników urządzeń pamięci masowej. To ustawienie dotyczy tylko systemów Windows XP i Windows Server 2003. Akcja wypełnia sekcję [SysprepMassStorage] pliku sysprep.inf przy użyciu informacji o wszystkich sterownikach pamięci masowej obsługiwanych przez obraz do przechwycenia.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDKeepActivation<br /><br /> (dane wejściowe)|Określa, czy program sysprep resetuje flagę aktywacji produktu.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDTargetSystemRoot<br /><br /> (dane wyjściowe)|Określa ścieżkę do katalogu zainstalowanego systemu operacyjnego Windows na komputerze odniesienia. Ten system operacyjny jest weryfikowany jako możliwy do przechwycenia obsługiwanego systemu operacyjnego przez program Configuration Manager.|  

###  <a name="BKMK_ReleaseStateStore"></a> Zmienne akcji sekwencji Zwolnij magazyn stanów  
 Zmienne tej akcji określają informacje używane do zwolnienia zapisanego stanu użytkownika. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Zwolnij Magazyn stanów](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (dane wejściowe)|Nazwa ścieżki UNC lub lokalnej dla lokalizacji, z której jest przywracany stan użytkownika. Ta wartość jest używana przez akcje sekwencji zadań **Przechwyć stan użytkownika** i **Przywróć stan użytkownika** .|  

###  <a name="BKMK_RequestState"></a> Zmienne akcji sekwencji zadań Zażądaj magazynu stanów  
 Zmienne tej akcji określają informacje używane do żądania zapisanego stanu użytkownika, takie jak folder w punkcie migracji stanu, w którym są przechowywane dane użytkownika. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Zwolnij Magazyn stanów](../../osd/understand/task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateFallbackToNAA<br /><br /> (dane wejściowe)|Określa, czy konto dostępu do sieci jest używane jako rezerwowe w przypadku, gdy konto komputera nie może nawiązać połączenia z punktem migracji stanu.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDStateSMPRetryCount<br /><br /> (dane wejściowe)|Określa liczbę prób znalezienia punktu migracji stanu przez krok sekwencji zadań, po której krok zakończy się niepowodzeniem. Określona liczba musi wynosić od 0 do 600.|  
|OSDStateSMPRetryTime<br /><br /> (dane wejściowe)|Określa liczbę sekund oczekiwania przez krok sekwencji zadań między ponownymi próbami. Wartość liczby sekund może zawierać maksymalnie 30 znaków.|  
|OSDStateStorePath<br /><br /> (dane wyjściowe)|Ścieżka UNC do folderu w punkcie migracji stanu, w którym jest przechowywany stan użytkownika.|  

###  <a name="BKMK_RestartComputer"></a> Zmienne akcji sekwencji zadań Uruchom ponownie komputer  
 Zmienne tej akcji określają informacje używane do ponownego uruchomienia komputera docelowego. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Uruchom ponownie komputer](task-sequence-steps.md#BKMK_RestartComputer).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|SMSRebootMessage<br /><br /> (dane wejściowe)|Określa komunikat, który ma być wyświetlany użytkownikom przed ponownym uruchomieniem komputera docelowego. Jeśli ta zmienna nie jest ustawiona, jest wyświetlany domyślny tekst komunikatu. Określony komunikat nie może przekraczać 512 znaków.<br /><br /> Przykład:<br /><br /> -"Ten komputer zostanie uruchomiony ponownie; Zapisz swoją pracę."|  
|SMSRebootTimeout<br /><br /> (dane wejściowe)|Określa liczbę sekund wyświetlania ostrzeżenia dla użytkownika przed ponownym uruchomieniem komputera. Określ zero sekund, aby wskazać, że komunikat o ponownym rozruchu nie ma być wyświetlany.<br /><br /> Przykłady:<br /><br /> **„0”** (domyślnie)<br /><br /> **„5”**<br /><br /> **„10”**|  

###  <a name="BKMK_RestoreUserState"></a> Zmienne akcji sekwencji zadań Przywróć stan użytkownika  
 Zmienne tej akcji określają informacje służące do przywrócenia stanu użytkownika komputera docelowego, takie jak nazwa ścieżki folderu, z którego jest przywracany stan, i czy jest przywracane konto komputera lokalnego. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Przywróć stan użytkownika](task-sequence-steps.md#BKMK_RestoreUserState).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (dane wejściowe)|Nazwa ścieżki UNC lub lokalnej dla folderu, z którego jest przywracany stan użytkownika.|  
|OSDMigrateContinueOnRestore<br /><br /> (dane wejściowe)|Określa, czy przywracanie stanu użytkownika jest kontynuowane, nawet jeśli nie można przywrócić niektórych plików.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”** (domyślna)<br /><br /> **„false”**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (dane wejściowe)|Włącza pełne rejestrowanie dla narzędzia USMT. Ta wartość jest wymagana przez akcję. Musi być ona równa „true” lub „false”.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDMigrateLocalAccounts<br /><br /> (dane wejściowe)|Określa, czy konto komputera lokalnego jest przywracane.<br /><br /> Prawidłowe wartości:<br /><br /> **„true”**<br /><br /> **„false”** (domyślnie)|  
|OSDMigrateLocalAccountPassword<br /><br /> (dane wejściowe)|Jeśli **zmienna OSDMigrateLocalAccounts** zmienna ma wartość "PRAWDA," Ta zmienna musi zawierać hasło, które jest przypisane do wszystkich migrowanych kont lokalnych. Ponieważ to samo hasło jest przypisany do wszystkich migrowanych kont lokalnych, jest traktowane jako hasło tymczasowe, które zostanie później zmienione za pomocą metody innej niż wdrożenie systemu operacyjnego programu Configuration Manager.|  
|OSDMigrateAdditionalRestoreOptions<br /><br /> (dane wejściowe)|Określa dodatkowe opcje wiersza polecenia narzędzia do migracji stanu użytkowników (USMT), które są używane podczas przywracania stanu użytkownika. Dodatkowe opcje są określone w postaci ciągu, który jest dołączany do automatycznie wygenerowanego wiersza polecenia narzędzia USMT. Opcje narzędzia USMT określone za pomocą tej zmiennej sekwencji zadań nie są weryfikowane pod kątem dokładności przed uruchomieniem sekwencji zadań.|  
|_OSDMigrateUsmtRestorePackageID<br /><br /> (dane wejściowe)|Określa identyfikator pakietu pakietu programu Configuration Manager, który zawiera pliki narzędzia USMT. Ta zmienna jest wymagana.|  

###  <a name="BKMK_RunCommand"></a> Zmienne akcji sekwencji zadań Uruchom wiersz polecenia  
 Zmienne tej akcji określają informacje używane do uruchomienia polecenia z wiersza polecenia, takie jak katalog roboczy, w którym jest uruchamiane polecenie. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Uruchom wiersz polecenia](task-sequence-steps.md#BKMK_RunCommandLine).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|SMSTSDisableWow64Redirection<br /><br /> (dane wejściowe)|Domyślnie w przypadku uruchomienia w 64-bitowym systemie operacyjnym program podany w wierszu polecenia jest wyszukiwany i uruchamiany za pomocą przekierowania systemu plików WOW64, dzięki czemu może znaleźć 32-bitowe wersje programów i bibliotek DLL systemu operacyjnego. Ustawienie tej zmiennej na wartość "true" powoduje wyłączenie readresatora systemu plików WOW64, tak, aby można było znaleźć macierzyste wersje 64-bitowego systemu operacyjnego, programów i bibliotek DLL. Ta zmienna nie ma znaczenia w przypadku uruchomienia w 32-bitowym systemie operacyjnym.|  
|WorkingDirectory<br /><br /> (dane wejściowe)|Określa katalog początkowy dla akcji wiersza polecenia. Nazwa określonego katalogu nie może przekraczać 255 znaków.<br /><br /> Przykłady:<br /><br /> -   **"C:\\"**<br />-   **„%SystemRoot%”**|  
|SMSTSRunCommandLineUserName<br /><br /> (dane wejściowe)|Określa konto, za pomocą którego jest uruchamiany wiersz polecenia. Wartość jest ciągiem w formacie nazwa_użytkownika lub domena\nazwa_użytkownika.|  
|SMSTSRunCommandLinePassword<br /><br /> (dane wejściowe)|Określa hasło konta wskazanego przez zmienną SMSTSRunCommandLineUserName.|  

### <a name="set-dynamic-variables"></a>Ustaw zmienne dynamiczne  
 Zmienne dla tej akcji są ustawiane automatycznie po dodaniu kroku sekwencji zadań Ustaw zmienne dynamiczne. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Ustaw zmienne dynamiczne](task-sequence-steps.md#BKMK_SetDynamicVariables).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|_SMSTSMake|Określa markę komputera.|  
|_SMSTSModel|Określa model komputera.|  
|_SMSTSMacAddresses|Określa adresy MAC używane przez komputer.|  
|_SMSTSIPAddresses|Określa adresy IP używane przez komputer.|  
|_SMSTSSerialNumber|Określa numer seryjny komputera.|  
|_SMSTSAssetTag|Określa tag zasobu komputera.|  
|_SMSTSUUID|Określa identyfikator UUID komputera.|  
|_SMSTSDefaultGateways|Określa bramy domyślne używane przez komputer.|  

###  <a name="BKMK_SetupWindows"></a> Zmienne akcji sekwencji zadań Zainstaluj system Windows i program ConfigMgr  
 Zmienna tej akcji określa właściwości instalacji klienta, które są używane podczas instalowania klienta programu Configuration Manager. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tymi zmiennymi, zobacz [Zainstaluj system Windows i program ConfigMgr](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|SMSClientInstallProperties<br /><br /> (dane wejściowe)|Określa właściwości instalacji klienta, które są używane podczas instalowania klienta programu Configuration Manager.|  

### <a name="upgrade-operating-system"></a>Uaktualnij system operacyjny  
 Zmienna tej akcji określa dodatkowe opcje wiersza polecenia, które nie są dostępne w programie Configuration Manager konsoli są dodawane do Instalatora do uaktualnienia systemu Windows 10. Aby uzyskać więcej informacji o kroku sekwencji zadań skojarzonym z tą zmienną, zobacz [Uaktualnij System operacyjny](task-sequence-steps.md#BKMK_UpgradeOS).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|OSDSetupAdditionalUpgradeOptions<br /><br /> (dane wejściowe)|Określa dodatkowe opcje wiersza polecenia, które są dodawane do instalatora podczas uaktualniania do systemu Windows 10. Opcje wiersza polecenia nie są weryfikowane. Dlatego sprawdź, czy wprowadzona opcja jest prawidłowa.<br /><br /> Aby uzyskać więcej informacji, zobacz [Opcje wiersza polecenia Instalatora systemu Windows](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx).|  
