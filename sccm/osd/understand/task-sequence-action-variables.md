---
title: "Zmienne akcji sekwencji zadań"
titleSuffix: Configuration Manager
description: "Zmienne akcji sekwencji, takich jak ustawienia sieci zmiennych, umożliwia określenie ustawień konfiguracyjnych dla jednego kroku w sekwencji zadań programu Configuration Manager."
ms.custom: na
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2269031-0977-4f01-a274-420e00630575
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2928ecb254d08e4ed08c5e79b55e210ce25dcb61
ms.sourcegitcommit: fbde417e3c3002898bd216a7e110e725ae269893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2018
---
# <a name="task-sequence-action-variables-in-system-center-configuration-manager"></a>Zmienne akcji sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zmienne akcji sekwencji zadań Określ ustawienia konfiguracji, które są używane przez pojedynczy krok w sekwencji zadań w programie System Center Configuration Manager. Domyślnie sekwencja zadań inicjuje jego ustawienia przed uruchomieniem. Te ustawienia są dostępne tylko podczas kroku sekwencji zadań skojarzona. Innymi słowy sekwencja zadań dodaje wartość zmiennej akcji do środowiska sekwencji zadań przed uruchomieniem kroku sekwencji zadań. Sekwencja zadań Usuwa wartość ze środowiska, po uruchomieniu tego kroku.  

## <a name="action-variable-example"></a>Przykład zmiennej akcji  
 Na przykład możesz określić katalog uruchomienia dla akcji wiersza polecenia za pomocą kroku sekwencji zadań **Uruchom wiersz polecenia** . Ten krok obejmuje właściwość **Rozpocznij w** , której domyślna wartość jest przechowywana w środowisku sekwencji zadań jako zmienna **WorkingDirectory** . Zmienna środowiskowa **WorkingDirectory** jest inicjowana przed uruchomieniem akcji sekwencji zadań **Uruchom wiersz polecenia** . Podczas kroku **Uruchom wiersz polecenia** wartość **WorkingDirectory** jest dostępna przez właściwość **Rozpocznij w** . Po ukończeniu tego kroku sekwencji zadań Usuwa wartość **WorkingDirectory** zmiennej ze środowiska. Jeśli sekwencja zawiera inny **Uruchom wiersz polecenia** krok sekwencji zadań, sekwencja zadań inicjuje nowy **WorkingDirectory** zmienną i ustawia go do początkową wartość dla bieżącego etapu.  

 *Domyślne* wartość dla zmiennej akcji sekwencji zadań jest obecnie po uruchomieniu kroku sekwencji zadań. Jeśli ustawisz *nowe* wartości, jest dostępny dla wielu kroków w sekwencji zadań. Jeśli użyjesz jednej z metod tworzenia zmiennej sekwencji zadań do przesłonięcia wbudowanej wartości zmiennej, nowa wartość pozostanie w środowisku i będzie przesłaniać wartość domyślną dla innych kroków sekwencji zadań. Na przykład, jeśli dodasz **Ustaw zmienną sekwencji zadań** krok w pierwszym kroku sekwencji zadań ustawia **WorkingDirectory** zmienną **C:\\**, wszelkie **Uruchom wiersz polecenia** kroku w sekwencji zadań korzysta z nowej wartości katalogu początkowego.  

## <a name="action-variables-for-task-sequence-actions"></a>Zmienne akcji dla akcji sekwencji zadań  
 Zmienne sekwencji zadań programu Configuration Manager są pogrupowane według ich skojarzonych akcji sekwencji zadań. Użyj następujących linków, aby zebrać informacje dotyczące zmiennych akcji skojarzonych z konkretną akcją. Zmienne sekwencji zadania określają sposób realizacji akcji sekwencji zadania. Akcja sekwencji zadania odczytuje i używa zmiennych oznaczonych przez użytkownika jako zmienne wejściowe. Alternatywnie można użyć [Ustaw zmienną sekwencji zadań](task-sequence-steps.md#BKMK_SetTaskSequenceVariable) krok lub obiektu TSEnvironment com. można ustawić zmienne w czasie wykonywania. Akcja sekwencji zadania oznacza zmienne jako zmienne wyjściowe. Te zmienne wyjściowe do odczytu akcje występujące później w sekwencji zadań.  

> [!NOTE]  
>  Nie wszystkie akcje sekwencji zadań są skojarzone ze zbiorem zmiennych sekwencji zadań. Na przykład mimo że istnieją zmienne skojarzone z akcją Włącz funkcję BitLocker, nie ma zmiennych skojarzonych z akcją Wyłącz funkcję BitLocker.  



###  <a name="BKMK_ApplyDataImage"></a>Zastosuj obraz danych   
 Aby uzyskać więcej informacji, zobacz [Zastosuj obraz danych](task-sequence-steps.md#BKMK_ApplyDataImage). 

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDDataImageIndex<br /><br /> (dane wejściowe)|Określa wartość indeksu obrazu, który zostanie zastosowany dla komputera docelowego.|  
|OSDWipeDestinationPartition<br /><br /> (dane wejściowe)|Określa, czy pliki znajdujące się na partycji docelowej zostaną usunięte.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  



###  <a name="BKMK_ApplyDriverPackage"></a>Zastosuj pakiet sterowników   
Aby uzyskać więcej informacji, zobacz [zastosuj pakiet sterowników](task-sequence-steps.md#BKMK_ApplyDriverPackage).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDApplyDriverBootCriticalContentUniqueID<br /><br /> (dane wejściowe)|Określa identyfikator zawartości sterownika urządzenia pamięci masowej do zainstalowania z pakietu sterowników. Jeśli ta zmienna nie zostanie określony, żaden sterownik pamięci masowej jest zainstalowany.|  
|OSDApplyDriverBootCriticalINFFile<br /><br /> (dane wejściowe)|Określa plik INF sterownika pamięci masowej do zainstalowania.<br /><br /> <br /><br /> Ta zmienna sekwencji zadań jest wymagana, jeśli ustawiono zmienną OSDApplyDriverBootCriticalContentUniqueID.|  
|OSDApplyDriverBootCriticalHardwareComponent<br /><br /> (dane wejściowe)|Określa, czy jest zainstalowany sterownik urządzenia pamięci masowej, ta zmienna musi być **scsi**.<br /><br /> Ta zmienna sekwencji zadań jest wymagana, jeśli ustawiono zmienną OSDApplyDriverBootCriticalContentUniqueID.|  
|OSDApplyDriverBootCriticalID<br /><br /> (dane wejściowe)|Określa identyfikator o krytycznym znaczeniu dla rozruchu dla sterownika urządzenia pamięci masowej do zainstalowania. Ten identyfikator jest wymieniony w **scsi** pliku txtsetup.oem sterownika urządzenia.<br /><br /> Ta zmienna sekwencji zadań jest wymagana, jeśli ustawiono zmienną OSDApplyDriverBootCriticalContentUniqueID.|  
|OSDAllowUnsignedDriver<br /><br /> (dane wejściowe)|Określa, czy system Windows ma zezwalać na instalowanie niepodpisanych sterowników urządzeń. Ta zmienna sekwencji zadań nie jest używana podczas wdrażania systemu Windows Vista i nowszych systemów operacyjnych.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  



###  <a name="BKMK_ApplyNetworkSettings"></a>Zastosuj ustawienia sieci   
 Aby uzyskać więcej informacji, zobacz [Zastosuj ustawienia sieci](task-sequence-steps.md#BKMK_ApplyNetworkSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDAdapter<br /><br /> (dane wejściowe)|Ta zmienna sekwencji zadań jest zmienną tablicową. Każdy element tablicy reprezentuje ustawienia jednej karty sieciowej w komputerze. Dostęp do ustawienia dla każdej karty przez połączenie nazwy zmiennej tablicowej z indeksem karty sieciowej liczonym od 0 i nazwą właściwości.<br /><br />Jeśli ten krok obejmuje skonfigurowanie wielu kart sieciowych, definiuje właściwości drugiej karty sieciowej przy użyciu indeksu w nazwie zmiennej. Na przykład OSDAdapter1EnableDHCP, OSDAdapter1IPAddressList, OSDAdapter1DNSDomain, OSDAdapter1WINSServerList i OSDAdapter1EnableWINS.<br /><br />Na przykład użyć następujące nazwy zmiennych do zdefiniowania właściwości pierwszej karty sieciowej dla tego kroku sekwencji zadań do skonfigurowania:<br /><br /> <ul><li>**OSDAdapter0EnableDHCP**: **true** włącza protokół dynamicznej konfiguracji hosta (DHCP) dla karty.<br />    To ustawienie jest wymagane. Możliwe wartości to: **Wartość true,** lub **False**.</li><li>**OSDAdapter0IPAddressList**: Rozdzielana przecinkami lista adresów IP dla karty. Ta właściwość jest ignorowana, chyba że właściwość **EnableDHCP** jest ustawiona na wartość **false**.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0SubnetMask**: Rozdzielana przecinkami lista masek podsieci. Ta właściwość jest ignorowana, chyba że właściwość **EnableDHCP** jest ustawiona na wartość **false**.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0Gateways**: Rozdzielana przecinkami lista adresów IP bramy. Ta właściwość jest ignorowana, chyba że właściwość **EnableDHCP** jest ustawiona na wartość **false**.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0DNSDomain**: Domena nazw System (DNS) domeny dla karty.</li><li>**OSDAdapter0DNSServerList**: Rozdzielana przecinkami lista serwerów DNS dla karty.<br />    To ustawienie jest wymagane.</li><li>**OSDAdapter0EnableDNSRegistration**: **true** powoduje zarejestrowanie adresu IP karty w systemie DNS.</li><li>**OSDAdapter0EnableFullDNSRegistration**: **true** można zarejestrować adresu IP karty w usłudze DNS pod pełną nazwą DNS dla komputera.</li><li>**OSDAdapter0EnableIPProtocolFiltering**: **true** umożliwiające filtrowania protokołu IP na karcie.</li><li>**OSDAdapter0IPProtocolFilterList**: Rozdzielana przecinkami lista protokołów, które mogą być uruchamiane przy użyciu protokołu IP. Ta właściwość jest ignorowana, jeśli właściwość **EnableIPProtocolFiltering** jest ustawiona na wartość **false**.</li><li>**OSDAdapter0EnableTCPFiltering**: **true** Aby włączyć port TCP filtrowania dla karty.</li><li>**OSDAdapter0TCPFilterPortList**: Rozdzielana przecinkami lista portów, które mogą mieć uprawnienia dostępu dla protokołu TCP. Ta właściwość jest ignorowana, jeśli właściwość **EnableTCPFiltering** jest ustawiona na wartość **false**.</li><li>**OSDAdapter0TcpipNetbiosOptions**: Opcje systemu NetBIOS przez TCP/IP. Dopuszczalne są następujące wartości:<br /><br /> <ul><li>**0**: Użyj ustawień NetBIOS z serwera DHCP.</li><li>**1**: Włącz system NetBIOS przez TCP/IP.</li><li>**2**: Wyłącz system NetBIOS przez TCP/IP.</li></ul></li><li>**OSDAdapter0EnableWINS**: **true** do korzystania z usługi WINS do rozpoznawania nazw.</li><li>**OSDAdapter0WINSServerList**: Rozdzielana przecinkami lista adresów IP serwerów WINS. Ta właściwość jest ignorowana, chyba że właściwość **EnableWINS** jest ustawiona na wartość **true**.</li><li>**OSDAdapter0MacAddress**: Adres MAC używany do dopasowania ustawień do fizycznej karty sieciowej.</li><li>**OSDAdapter0Name**: Nazwa połączenia sieciowego wyświetlaną w programie Panelu sterowania połączeń sieciowych. Nazwa ma od 0 do 255 znaków długości.</li><li>**OSDAdapter0Index**: Indeks ustawień karty sieciowej w tablicy ustawień.<br /><br />     OSDAdapterCount=1<br />    OSDAdapter0EnableDHCP = FALSE<br />    OSDAdapter0IPAddressList=192.168.0.40<br />    OSDAdapter0SubnetMask=255.255.255.0<br />    OSDAdapter0Gateways=192.168.0.1<br />    OSDAdapter0DNSSuffix=contoso.com</li></ul>|  
|OSDAdapterCount<br /><br /> (dane wejściowe)|Określa liczbę kart sieciowych zainstalowanych w komputerze docelowym. Jeśli wartość **OSDAdapterCount** jest ustawiona, wszystkie opcje konfiguracji każdego adaptera muszą być ustawione. Na przykład jeśli ustawisz wartość **OSDAdapterTCPIPNetbiosOptions** dla określonej karty, to wszystkie wartości dla tej karty muszą również zostać skonfigurowane.<br /><br />Jeśli ta wartość nie jest określona, wszystkie wartości **OSDAdapter** są ignorowane.|  
|OSDDNSDomain<br /><br /> (dane wejściowe)|Określa podstawowy serwer DNS, który jest używany przez komputer docelowy.|  
|OSDDomainName<br /><br /> (dane wejściowe)|Określa nazwę domeny systemu Windows, do której jest przyłączany komputer docelowy. Określona wartość musi być prawidłową nazwą domeny usług domenowych Active Directory.|  
|OSDDomainOUName<br /><br /> (dane wejściowe)|Określa nazwę jednostki organizacyjnej (OU), do której jest przyłączany komputer docelowy, w formacie RFC 1779. Jeśli wartość jest określona, musi zawierać pełną ścieżkę.<br /><br /> Przykład:<br /><br /> **LDAP://OU=MojaJO,DC=MojaDomena,DC=MojaFirma,DC=com**|  
|OSDEnableTCPIPFiltering<br /><br /> (dane wejściowe)|Określa, czy filtrowanie protokołu TCP/IP jest włączone.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDJoinAccount<br /><br /> (dane wejściowe)|Określa konto sieciowe, które służy do dodawania komputera docelowego do domeny systemu Windows.|  
|OSDJoinPassword<br /><br /> (dane wejściowe)|Określa hasło dostępu do sieci, które służy do dodawania komputera docelowego do domeny systemu Windows.|  
|OSDNetworkJoinType<br /><br /> (dane wejściowe)|Określa, czy komputer docelowy jest przyłączany do domeny systemu Windows lub grupy roboczej.<br /><br /> **0** wskazuje, że komputer docelowy jest dołączany do domeny systemu Windows. **1** Określa, czy komputer jest przyłączony do grupy roboczej.<br /><br /> Prawidłowe wartości:<br /><br /> **0**<br /><br /> **1**|  
|OSDDNSSuffixSearchOrder<br /><br /> (dane wejściowe)|Określa kolejność wyszukiwania w usłudze DNS dla komputera docelowego.|  
|OSDWorkgroupName<br /><br /> (dane wejściowe)|Określa nazwę grupy roboczej, do której jest przyłączany komputer docelowy.<br /><br /> Określić albo tę wartość lub **zmiennej OSDDomainName** wartość. Nazwa grupy roboczej może mieć maksymalnie 32 znaki.<br /><br /> Przykład:<br /><br /> **Ewidencjonowanie aktywności**|  



###  <a name="BKMK_ApplyOperatingSystem"></a>Zastosuj obraz systemu operacyjnego   
 Aby uzyskać więcej informacji, zobacz [Zastosuj obraz systemu operacyjnego](task-sequence-steps.md#BKMK_ApplyOperatingSystemImage).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDConfigFileName<br /><br /> (dane wejściowe)|Określa nazwę pliku odpowiedzi wdrożenia systemu operacyjnego skojarzonego z pakietem wdrożenia systemu operacyjnego.|  
|OSDImageIndex<br /><br /> (dane wejściowe)|Określa wartość indeksu obrazu w pliku WIM, który zostanie zastosowany dla komputera docelowego.|  
|OSDInstallEditionIndex<br /><br /> (dane wejściowe)|Określa wersję systemu operacyjnego Windows Vista lub nowszego, który jest instalowany. Jeśli wersja nie jest określona, Instalator systemu Windows określa, którą wersję zainstalować, za pomocą odnośnego klucza produktu.<br /><br /> Użyj wartości zero (0), tylko jeśli są spełnione następujące warunki:<br /><br /> -Instalowany jest systemem operacyjnym starszym niż Windows Vista<br />— W przypadku instalowania wersji używającej licencji zbiorczej systemu Windows Vista lub nowszy, a klucz produktu nie jest określony.<br /><br /> Prawidłowe wartości:<br /><br /> **0** (ustawienie domyślne)|  
|OSDTargetSystemDrive (dane wyjściowe)|Określa literę dysku partycji zawierającej pliki systemu operacyjnego.|  



###  <a name="BKMK_ApplyWindowsSettings"></a>Zastosuj ustawienia systemu Windows   
 Aby uzyskać więcej informacji, zobacz [Zastosuj ustawienia systemu Windows](task-sequence-steps.md#BKMK_ApplyWindowsSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDComputerName<br /><br /> (dane wejściowe)|Określa nazwę komputera docelowego.<br /><br /> Przykład:<br /><br /> **%_SMSTSMachineName%** (default)|  
|OSDProductKey<br /><br /> (dane wejściowe)|Określa klucz produktu systemu Windows. Określona wartość musi mieć od 1 do 255 znaków.|  
|OSDRegisteredUserName<br /><br /> (dane wejściowe)|Określa domyślną nazwę zarejestrowanego użytkownika w nowym systemie operacyjnym. Określona wartość musi mieć od 1 do 255 znaków.|  
|OSDRegisteredOrgName<br /><br /> (dane wejściowe)|Określa domyślną nazwę zarejestrowanej organizacji w nowym systemie operacyjnym. Określona wartość musi mieć od 1 do 255 znaków.|  
|OSDTimeZone<br /><br /> (dane wejściowe)|Określa domyślne ustawienie strefy czasowej używane w nowym systemie operacyjnym.|  
|OSDServerLicenseMode<br /><br /> (dane wejściowe)|Określa używany tryb licencji systemu Windows Server.<br /><br /> Prawidłowe wartości:<br /><br /> **PerSeat**<br /><br /> **PerServer**|  
|OSDServerLicenseConnectionLimit<br /><br /> (dane wejściowe)|Określa maksymalną dozwoloną liczbę połączeń. Określona liczba musi być w zakresie od 5 do 9999 połączeń.|  
|OSDRandomAdminPassword<br /><br /> (dane wejściowe)|Określa losowo wygenerowane hasło dla konta administratora w nowym systemie operacyjnym. Jeśli ustawiono **true**, Instalator systemu Windows powoduje wyłączenie konta administratora lokalnego na komputerze docelowym. Jeśli ustawiono **false**, Instalator systemu Windows umożliwia konta administratora lokalnego na komputerze docelowym i ustawia hasło konta z wartością **OSDLocalAdminPassword**.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  
|OSDLocalAdminPassword<br /><br /> (dane wejściowe)|Określa hasło administratora lokalnego. Po włączeniu **losowo Generuj hasło administratora lokalnego i Wyłącz konto na wszystkich obsługiwanych platformach**, następnie kroku ignoruje tej zmiennej. Określona wartość musi mieć od 1 do 255 znaków.|  



###  <a name="BKMK_AutoApplyDrivers"></a>Automatycznie Zastosuj sterowniki   
 Aby uzyskać więcej informacji, zobacz [automatycznie Zastosuj sterowniki](task-sequence-steps.md#BKMK_AutoApplyDrivers).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDAutoApplyDriverCategoryList<br /><br /> (dane wejściowe)|Rozdzielana przecinkami lista unikatowych identyfikatorów kategorii katalogu sterownika. **Automatycznie Zastosuj sterownik** krok uwzględnia tylko sterowniki w co najmniej jeden z określonych kategorii. Ta wartość jest opcjonalna i domyślnie nie jest ustawiona. Uzyskaj dostępne identyfikatory kategorii wyliczając listę **SMS_CategoryInstance** obiektów w lokacji.|  
|OSDAllowUnsignedDriver<br /><br /> (dane wejściowe)|Określa, czy konfiguracja systemu Windows zezwala na instalowanie niepodpisanych sterowników urządzeń. Ta zmienna sekwencji zadań nie jest używana podczas wdrażania systemu operacyjnego Windows Vista i nowszych.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDAutoApplyDriverBestMatch<br /><br /> (dane wejściowe)|Jeśli istnieje wiele sterowników urządzeń w katalogu sterowników, które są zgodne z urządzeniem sprzętowym, ta zmienna Określa działanie etapu. Jeśli ustawiono **true**, kroku instaluje tylko najlepszy sterownik urządzenia. Jeśli **false**kroku są instalowane wszystkie zgodne sterowniki urządzenia i system Windows wybiera najlepszy sterownik do użycia.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  
|SMSTSDriverRequestConnectTimeOut|Podczas żądania z katalogu sterowników, ta zmienna jest liczbę sekund, sekwencja zadań czeka na połączenie z serwerem HTTP. Jeśli połączenie trwa dłużej niż ustawienie limitu czasu, sekwencja zadań anuluje żądanie. Domyślnie limit czasu ma ustawioną wartość **60** sekund.|  
|SMSTSDriverRequestReceiveTimeOut|Podczas żądania z katalogu sterowników, ta zmienna jest liczbę sekund, przez które sekwencja zadań czeka na odpowiedź. Jeśli połączenie trwa dłużej niż ustawienie limitu czasu, sekwencja zadań anuluje żądanie. Domyślnie limit czasu ma ustawioną wartość **480** sekund.|
|SMSTSDriverRequestResolveTimeOut|Podczas żądania z katalogu sterowników, ta zmienna jest liczbę sekund oczekiwania przez sekwencję zadań do rozpoznawania nazw protokołu HTTP. Jeśli połączenie trwa dłużej niż ustawienie limitu czasu, sekwencja zadań anuluje żądanie. Domyślnie limit czasu ma ustawioną wartość **60** sekund.|
|SMSTSDriverRequestSendTimeOut|Podczas wysyłania żądania do katalogu sterowników, ta zmienna jest liczbę sekund oczekiwania przez sekwencję zadań można wysłać żądania. Jeśli wykonywanie żądania trwa dłużej niż ustawienie limitu czasu, sekwencja zadań anuluje żądanie. Domyślnie limit czasu ma ustawioną wartość **60** sekund.|



###  <a name="BKMK_CaptureNetworkSettings"></a>Przechwyć ustawienia sieci   
 Aby uzyskać więcej informacji, zobacz [Przechwyć ustawienia sieci](task-sequence-steps.md#BKMK_CaptureNetworkSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDMigrateAdapterSettings<br /><br /> (dane wejściowe)|Określa, czy informacje o konfiguracji ustawień karty sieciowej (TCP/IP, DNS i WINS) są przechwytywane.<br /><br /> Przykłady:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  
|OSDMigrateNetworkMembership<br /><br /> (dane wejściowe)|Określa, czy informacje o przynależności do grupy roboczej lub domeny są migrowane w ramach wdrożenia systemu operacyjnego.<br /><br /> Przykłady:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  



###  <a name="BKMK_CaptureOperatingSystemImage"></a>Przechwyć obraz systemu operacyjnego   
 Aby uzyskać więcej informacji, zobacz [Przechwyć obraz systemu operacyjnego](task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  

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



###  <a name="BKMK_CaptureUserState"></a>Przechwyć stan użytkownika   
 Aby uzyskać więcej informacji, zobacz [Przechwyć stan użytkownika](task-sequence-steps.md#BKMK_CaptureUserState).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (dane wejściowe)|Nazwa ścieżki UNC lub ścieżki lokalnej folderu, w którym jest zapisany stan użytkownika. Brak wartości domyślnej.|  
|OSDMigrateAdditionalCaptureOptions<br /><br /> (dane wejściowe)|Dodatkowe opcje migracji stanu użytkowników (USMT) Narzędzie wiersza polecenia używane przez sekwencję zadań w celu przechwycenia stanu użytkownika. Krok nie ujawnia tych ustawień w edytorze sekwencji zadań. Te opcje jako ciąg, sekwencja zadań dołącza do automatycznie generowanego wiersza polecenia USMT.<br /><br />Opcje narzędzia USMT określone za pomocą tej zmiennej sekwencji zadań nie są weryfikowane pod kątem dokładności przed uruchomieniem sekwencji zadań.|  
|OSDMigrateMode<br /><br /> (dane wejściowe)|Umożliwia dostosowanie plików przechwytywanych przez narzędzie USMT. Jeśli ta zmienna jest ustawiona **proste**, a następnie sekwencja zadań używa tylko standardowe pliki konfiguracji narzędzia USMT. Jeśli ta zmienna jest ustawiona **zaawansowane**, a następnie zmienną sekwencji zadań OSDMigrateConfigFiles Określa pliki konfiguracyjne, które korzysta z narzędzia USMT.<br /><br /> Prawidłowe wartości:<br /><br /> **Proste**<br /><br /> **Zaawansowane**|  
|OSDMigrateConfigFiles<br /><br /> (dane wejściowe)|Określa pliki konfiguracji służące do kontrolowania przechwytywania profilów użytkowników. Ta zmienna jest używana tylko wtedy gdy zmienna OSDMigrateMode jest ustawiona na Zaawansowane. Ta wartość określająca rozdzielaną przecinkami listę jest ustawiana na potrzeby wykonania niestandardowej migracji profilu użytkownika.<br /><br /> Przykład: miguser.xml,migsys.xml,migapps.xml|  
|OSDMigrateContinueOnLockedFiles<br /><br /> (dane wejściowe)|Jeśli narzędzie USMT nie można przechwycić niektórych plików, ta zmienna umożliwia kontynuowanie przechwytywania stanu użytkownika.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (dane wejściowe)|Włącza pełne rejestrowanie dla narzędzia USMT.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDMigrateSkipEncryptedFiles<br /><br /> (dane wejściowe)|Określa, czy zaszyfrowane pliki są przechwytywane.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|_OSDMigrateUsmtPackageID<br /><br /> (dane wejściowe)|Określa identyfikator pakietu pakietu programu Configuration Manager, który zawiera pliki narzędzia USMT. Ta zmienna jest wymagana.|  



###  <a name="BKMK_CaptureWindowsSettings"></a>Przechwyć ustawienia systemu Windows   
 Aby uzyskać więcej informacji, zobacz [Przechwyć ustawienia systemu Windows](task-sequence-steps.md#BKMK_CaptureWindowsSettings).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDMigrateComputerName<br /><br /> (dane wejściowe)|Określa, czy nazwa komputera jest migrowana.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**<br /><br /> Jeśli wartość jest **true**, zmienna OSDComputerName przybiera wartość nazwy NetBIOS komputera.|  
|OSDComputerName<br /><br /> (dane wyjściowe)|Ustawiona na nazwę NetBIOS komputera. Wartość jest ustawiona tylko wtedy, gdy zmienna OSDMigrateComputerName jest ustawiona **true**.|  
|OSDMigrateRegistrationInfo<br /><br /> (dane wejściowe)|Określa, czy krok migracji informacje o użytkowniku i organizacji.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**<br /><br /> Jeśli wartość jest **true**, zmienna OSDRegisteredOrgName przybiera wartość zarejestrowanej nazwy organizacji komputera.|  
|OSDRegisteredOrgName<br /><br /> (dane wyjściowe)|Ustawiona na nazwę zarejestrowanej organizacji komputera. Wartość jest ustawiona tylko wtedy, gdy zmienna OSDMigrateRegistrationInfo jest ustawiona **true**.|  
|OSDMigrateTimeZone<br /><br /> (dane wejściowe)|Określa, czy strefa czasowa komputera jest migrowana.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**<br /><br /> Jeśli wartość jest **true**, zmienna OSDTimeZone przybiera wartość strefy czasowej komputera.|  
|OSDTimeZone<br /><br /> (dane wyjściowe)|Ustawiona na strefę czasową komputera. Wartość jest ustawiona tylko wtedy, gdy zmienna OSDMigrateTimeZone jest ustawiona **true**.|  



###  <a name="BKMK_ConnecttoNetworkFolder"></a>Połącz z folderem sieciowym   
 Aby uzyskać więcej informacji, zobacz [połączenia do folderu sieciowego](task-sequence-steps.md#BKMK_ConnectToNetworkFolder).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|SMSConnectNetworkFolderAccount<br /><br /> (dane wejściowe)|Określa konto administratora używane do nawiązania połączenia z udziałem sieciowym.|  
|SMSConnectNetworkFolderDriveLetter<br /><br /> (dane wejściowe)|Określa literę dysku sieciowego, z którym ma zostać nawiązane połączenie. Ta wartość jest opcjonalna. Jeśli nie zostanie określona, połączenie sieciowe nie zostanie zamapowane na literę dysku. Jeśli ta wartość jest określona, to musi należeć do zakresu od D: do Z:. Ponadto nie należy używać wartości X:, ponieważ jest to litera dysku używana przez środowisko Windows PE w fazie Windows PE.<br /><br /> Przykłady:<br /><br /> **D:**<br /><br /> **E:**|  
|SMSConnectNetworkFolderPassword<br /><br /> (dane wejściowe)|Określa hasło dostępu do sieci używane do nawiązania połączenia z udziałem sieciowym.|  
|SMSConnectNetworkFolderPath<br /><br /> (dane wejściowe)|Określa ścieżkę sieciową dla połączenia.<br /><br /> Przykład:<br /><br /> **\\\servername\sharename**|  



###  <a name="BKMK_EnableBitLocker"></a>Włącz funkcję BitLocker   
 Aby uzyskać więcej informacji, zobacz [Włącz funkcję BitLocker](task-sequence-steps.md#BKMK_EnableBitLocker).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDBitLockerRecoveryPassword<br /><br /> (dane wejściowe)|Zamiast generowania losowego hasła odzyskiwania akcja sekwencji zadań **Włącz funkcję BitLocker** używa określonej wartości jako hasła odzyskiwania. Wartość musi być prawidłowym liczbowym hasłem odzyskiwania funkcji BitLocker.|  
|OSDBitLockerStartupKey<br /><br /> (dane wejściowe)|Zamiast generowania losowego klucza uruchomienia dla opcji zarządzania kluczami **klucz uruchomienia tylko na USB** **Włącz funkcję BitLocker** krok używa modułu (TPM) jako klucza uruchomienia. Wartość musi być prawidłowym 256-bitowym kluczem uruchomienia funkcji BitLocker zakodowanym w formacie Base64.|  



###  <a name="BKMK_FormatPartitionDisk"></a>Format i partycji   
 Aby uzyskać więcej informacji, zobacz [Format i partycji](task-sequence-steps.md#BKMK_FormatandPartitionDisk).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDDiskIndex<br /><br /> (dane wejściowe)|Określa numer dysku fizycznego do podzielenia na partycje.|  
|OSDDiskpartBiosCompatibilityMode<br /><br /> (dane wejściowe)|Podczas partycjonowania dysku twardego w celu zapewnienia zgodności z pewnymi typami systemu BIOS, ta zmienna Określa, czy wyłączyć optymalizacje wyrównania pamięci podręcznej. Jest to konieczne w przypadku wdrażania systemów operacyjnych Windows XP lub Windows Server 2003. Aby uzyskać więcej informacji, zobacz [artykuł 931760](http://go.microsoft.com/fwlink/?LinkId=134081) i [artykuł 931761](http://go.microsoft.com/fwlink/?LinkId=134082) w bazie wiedzy Microsoft Knowledge Base.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)| 
|OSDGPTBootDisk<br /><br /> (dane wejściowe)|Określa, czy utworzyć partycję EFI na dysku twardym GPT. Komputery z interfejsem EFI używają tej partycji jako dysku startowego.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDPartitions<br /><br /> (dane wejściowe)|Określa tablicę ustawień partycji. Informacje na temat uzyskiwania dostępu do zmiennych tablicowych w środowisku sekwencji zadań zawiera temat dotyczący zestawu SDK.<br /><br /> Ta zmienna sekwencji zadań jest zmienną tablicową. Każdy element tablicy reprezentuje ustawienia jednej partycji na dysku twardym. Dostęp do ustawień zdefiniowane dla każdej partycji przez połączenie nazwy zmiennej tablicowej z numerem partycji dysku liczonym od 0 i nazwą właściwości.<br /><br /> Na przykład użyć następujące nazwy zmiennych do zdefiniowania właściwości pierwszej partycji, która w tym kroku zostanie utworzony na dysku twardym:<br /><br /> - **OSDPartitions0Type**: Określa typ partycji. Ta właściwość jest wymagana. Prawidłowe wartości to **głównej**, **rozszerzone**, **logiczne**, i **Hidden**.<br />-   **OSDPartitions0FileSystem**: Określa typ systemu plików do użycia podczas formatowania partycji. Ta właściwość jest opcjonalna. Jeśli system plików nie jest określony, kroku nie Formatuj partycję. Prawidłowe wartości to **FAT32** i **NTFS**.<br />-   **OSDPartitions0Bootable**: Określa, czy partycja jest partycją rozruchową. Ta właściwość jest wymagana. Jeśli ta wartość jest równa **TRUE** w przypadku dysków MBR kroku oznaczy wtedy tej partycji jako aktywne.<br />-   **OSDPartitions0QuickFormat**: Określa typ użytego formatu. Ta właściwość jest wymagana. Jeśli ta wartość jest równa **TRUE**, wykonuje kroku szybkie formatowanie. W przeciwnym razie krok przeprowadza pełne formatowanie.<br />-   **OSDPartitions0VolumeName**: Określa nazwę, która jest przypisana do woluminu, gdy jest on formatowany. Ta właściwość jest opcjonalna.<br />-   **OSDPartitions0Size**: Określa rozmiar partycji. Jednostki są określone przez zmienną **OSDPartitions0SizeUnits** . Ta właściwość jest opcjonalna. Jeśli ta właściwość nie jest określona, utworzona partycja będzie zajmowała całe wolne miejsce.<br />-   **OSDPartitions0SizeUnits**: Krok używa tych jednostek interpretować **OSDPartitions0Size** zmiennej. Ta właściwość jest opcjonalna. Prawidłowe wartości to **MB** (ustawienie domyślne), **GB**, i **procent**.<br />-   **OSDPartitions0VolumeLetterVariable**: Spowoduje to utworzenie partycji, zawsze używa następna dostępna litera dysku w środowisku Windows PE. Użyj tej opcjonalnej właściwości do określenia nazwy innej zmiennej sekwencji zadań. Krok używa tej zmiennej do zapisania litery nowego dysku do użytku w przyszłości.<br /><br />W przypadku definiowania wiele partycji z tej akcji sekwencji zadań, właściwości drugiej partycji są definiowane przy użyciu jej indeksu w nazwie zmiennej. Na przykład: **OSDPartitions1Type**, **OSDPartitions1FileSystem**, **OSDPartitions1Bootable**, **OSDPartitions1QuickFormat**, i  **OSDPartitions1VolumeName**.|  
|OSDPartitionStyle<br /><br /> (dane wejściowe)|Określa styl partycji do użycia podczas tworzenia partycji na dysku. **MBR** wskazuje na styl partycji rekordów główny i **GPT** wskazuje na styl z tabelą partycji GUID.<br /><br /> Prawidłowe wartości:<br /><br /> **GPT**<br /><br /> **MBR**|  



###  <a name="BKMK_InstallApplication"></a>Instalowanie aplikacji   
 Aby uzyskać więcej informacji, zobacz [zainstaluj aplikację](task-sequence-steps.md#BKMK_InstallApplication).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
| TSErrorOnWarning |Określ, czy aparat sekwencji zadań traktuje ostrzeżenie jako błąd w tym kroku. Sekwencja zadań ustawia zmienną _TSAppInstallStatus **ostrzeżenie** po co najmniej jedna aplikacja lub wymagana zależność nie został zainstalowany, ponieważ nie spełnia wymagania. Po ustawieniu tej zmiennej **True**, a sekwencja zadań ustawia _TSAppInstallStatus na ostrzeżenie, wynikiem jest błąd. Wartość **False** jest zachowaniem domyślnym.| 
|SMSTSMPListRequestTimeoutEnabled|Użyj tej zmiennej do żądań MPList odświeżyć klienta, jeśli klient nie znajduje się w intranecie. <br />Domyślnie ta zmienna jest ustawiona **True**. Jeśli klienci znajdują się w Internecie, można skonfigurować ustawienie tej zmiennej **False** aby zapobiec zbędnym opóźnieniom. Ta zmienna dotyczy tylko kroków sekwencji zadań Zainstaluj aplikację i Zainstaluj aktualizacje oprogramowania.|  
|SMSTSMPListRequestTimeout|Określ liczbę milisekund oczekiwania przez sekwencję zadań przed ponowną próbą zainstalowania aplikacji po niepowodzeniu pobrania zarządzania listy punktów z usług lokalizacji. Domyślnie sekwencja zadań czeka **60000** milisekund (60 sekund), zanim ponawia etap i ponowi próbę maksymalnie trzy razy.|  



###  <a name="BKMK_InstallSoftwareUpdates"></a>Instalacja aktualizacji oprogramowania   
Aby uzyskać więcej informacji, zobacz [Zainstaluj aktualizacje oprogramowania](task-sequence-steps.md#BKMK_InstallSoftwareUpdates).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|SMSInstallUpdateTarget<br /><br /> (dane wejściowe)|Określa, czy zainstalować wszystkie aktualizacje, czy tylko aktualizacje obowiązkowe.<br /><br /> Prawidłowe wartości:<br /><br /> **Wszystkie**<br /><br /> **Obowiązkowe**|  
|SMSTSSoftwareUpdateScanTimeout| Kontrola limitu czasu skanowania aktualizacji oprogramowania w tym kroku. Na przykład zwiększ wartość, jeśli wiele aktualizacji podczas skanowania. Wartość domyślna to **1800** sekund (30 minut). Wartość zmiennej jest ustawiana w sekundach. |
|SMSTSWaitForSecondReboot|Ta opcjonalna zmienna sekwencji zadań kontroluje zachowanie klienta podczas instalacji aktualizacji oprogramowania wymaga ponownego uruchomienia dwóch. Ustaw wartość tej zmiennej przed wykonaniem tej czynności, aby zapobiec niepowodzeniu sekwencji zadań z powodu drugiego ponownego uruchomienia od instalacji aktualizacji oprogramowania.<br /><br /> Należy ustawić wartość SMSTSWaitForSecondReboot w sekundach, aby określić, jak długo sekwencja zadań zatrzyma się w tym kroku podczas ponownego uruchomienia komputera. W przypadku braku drugiego ponownego uruchomienia, należy przewidzieć czas wystarczający. <br />Na przykład jeśli zmienna SMSTSWaitForSecondReboot zostanie ustawiona na 600, sekwencja zadań jest wstrzymywana przez 10 minut od ponownego uruchomienia komputera przed uruchomieniem dodatkowe kroki. Ta zmienna jest przydatne podczas jednego kroku sekwencji zadań Zainstaluj aktualizacje oprogramowania instalowania kilkuset aktualizacji oprogramowania.| 
|SMSTSMPListRequestTimeoutEnabled|Użyj tej zmiennej do żądań MPList odświeżyć klienta, jeśli klient nie znajduje się w intranecie. <br />Domyślnie ta zmienna jest ustawiona **True**. Jeśli klienci znajdują się w Internecie, można skonfigurować ustawienie tej zmiennej **False** aby zapobiec zbędnym opóźnieniom. Ta zmienna dotyczy tylko kroków sekwencji zadań Zainstaluj aplikację i Zainstaluj aktualizacje oprogramowania.|  
|SMSTSMPListRequestTimeout|Określ liczbę milisekund oczekiwania przez sekwencję zadań przed ponowną próbą zainstalowania aktualizacji oprogramowania po niepowodzeniu pobrania zarządzania listy punktów z usług lokalizacji. Domyślnie sekwencja zadań czeka **60000** milisekund (60 sekund), zanim ponawia etap i ponowi próbę maksymalnie trzy razy.|  



###  <a name="BKMK_JoinDomainWorkgroup"></a>Przyłącz do domeny lub grupy roboczej   
 Aby uzyskać więcej informacji, zobacz [Przyłącz do domeny lub grupy roboczej](task-sequence-steps.md#BKMK_JoinDomainorWorkgroup).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDJoinAccount<br /><br /> (dane wejściowe)|Określa konto, które jest używane przez komputer docelowy do przyłączenia do domeny usługi Active Directory. Ta zmienna jest wymagana w przypadku przyłączania do domeny.|  
|OSDJoinDomainName<br /><br /> (dane wejściowe)|Określa nazwę domeny usługi Active Directory komputera docelowego sprzężenia. Długość nazwy domeny musi należeć do zakresu od 1 do 255 znaków.|  
|OSDJoinDomainOUName<br /><br /> (dane wejściowe)|Określa nazwę jednostki organizacyjnej (OU), do której jest przyłączany komputer docelowy, w formacie RFC 1779. Jeśli wartość jest określona, musi zawierać pełną ścieżkę. Długość nazwy jednostki Organizacyjnej musi należeć do zakresu od 0 do 32 767 znaków. Ta wartość nie jest ustawiona, jeśli **OSDJoinType** zmienna jest ustawiona na **1** (Dołącz do grupy roboczej).<br /><br /> Przykład:<br /><br /> **LDAP://OU=MojaJO,DC=MojaDomena,DC=MojaFirma,DC=com**|  
|OSDJoinPassword<br /><br /> (dane wejściowe)|Określa hasło sieciowe, które korzysta z komputera docelowego do przyłączenia do domeny usługi Active Directory. Jeśli środowiska sekwencji zadań nie zawiera tej zmiennej, Instalator systemu Windows podejmie pustego hasła. Jeśli zmienna **OSDJoinType** zmienna jest ustawiona na **0** (przyłączenie do domeny), ta wartość jest wymagana.|  
|OSDJoinSkipReboot<br /><br /> (dane wejściowe)|Określa, czy pominąć ponowne uruchomienie po przyłączeniu komputera docelowego do domeny lub grupy roboczej.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **wartość false**|  
|OSDJoinType<br /><br /> (dane wejściowe)|Określa, czy komputer docelowy jest przyłączany do domeny systemu Windows lub grupy roboczej. Aby przyłączyć komputer docelowy do domeny systemu Windows, należy określić **0**. Aby przyłączyć komputer docelowy do grupy roboczej, określ **1**.<br /><br /> Prawidłowe wartości:<br /><br /> **0**<br /><br /> **1**|  
|OSDJoinWorkgroupName<br /><br /> (dane wejściowe)|Określa nazwę grupy roboczej, do której zostanie przyłączony komputer docelowy. Długość nazwy grupy roboczej musi wynosić od 1 do 32 znaków.<br /><br /> Przykład:<br /><br /> **Ewidencjonowanie aktywności**|  



###  <a name="BKMK_PrepareWindowsCapture"></a>Przygotuj system Windows do przechwycenia   
 Aby uzyskać więcej informacji, zobacz [Przygotuj system Windows do przechwycenia](task-sequence-steps.md#BKMK_PrepareWindowsforCapture).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDBuildStorageDriverList<br /><br /> (dane wejściowe)|Określa, czy program Sysprep tworzy listę sterowników urządzeń pamięci masowej. To ustawienie dotyczy tylko systemów Windows XP i Windows Server 2003. Ta zmienna wypełnia sekcję [SysprepMassStorage] pliku Sysprep.inf przy użyciu informacji na temat wszystkie sterowniki pamięci masowej, które są obsługiwane przez obraz do przechwycenia.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDKeepActivation<br /><br /> (dane wejściowe)|Określa, czy program sysprep resetuje flagę aktywacji produktu.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDTargetSystemRoot<br /><br /> (dane wyjściowe)|Określa ścieżkę do katalogu zainstalowanego systemu operacyjnego Windows na komputerze odniesienia. Ten system operacyjny jest weryfikowany jako możliwy do przechwycenia obsługiwanego systemu operacyjnego przez program Configuration Manager.|  



###  <a name="BKMK_ReleaseStateStore"></a>Zwolnij Magazyn stanów   
 Aby uzyskać więcej informacji, zobacz [Zwolnij Magazyn stanów](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (dane wejściowe)|Nazwa ścieżki UNC lub lokalnej dla lokalizacji, z której jest przywracany stan użytkownika. Ta wartość jest używana przez akcje sekwencji zadań **Przechwyć stan użytkownika** i **Przywróć stan użytkownika** .|  



###  <a name="BKMK_RequestState"></a>Zażądaj magazynu stanów   
  Aby uzyskać więcej informacji, zobacz [Zwolnij Magazyn stanów](task-sequence-steps.md#BKMK_ReleaseStateStore).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateFallbackToNAA<br /><br /> (dane wejściowe)|Gdy konto komputera nie może nawiązać połączenia z punktem migracji stanu, ta zmienna Określa, czy sekwencja zadań przechodzi do używają konta dostępu do sieci (ana).<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDStateSMPRetryCount<br /><br /> (dane wejściowe)|Określa liczbę prób znalezienia punktu migracji stanu przez krok sekwencji zadań, po której krok zakończy się niepowodzeniem. Określona liczba musi wynosić od 0 do 600.|  
|OSDStateSMPRetryTime<br /><br /> (dane wejściowe)|Określa liczbę sekund oczekiwania przez krok sekwencji zadań między ponownymi próbami. Wartość liczby sekund może zawierać maksymalnie 30 znaków.|  
|OSDStateStorePath<br /><br /> (dane wyjściowe)|Ścieżka UNC do folderu w punkcie migracji stanu, w którym jest przechowywany stan użytkownika.|  



###  <a name="BKMK_RestartComputer"></a>Uruchom ponownie komputer   
 Aby uzyskać więcej informacji, zobacz [Uruchom ponownie komputer](task-sequence-steps.md#BKMK_RestartComputer).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|SMSRebootMessage<br /><br /> (dane wejściowe)|Określa komunikat, który ma być wyświetlany użytkownikom przed ponownym uruchomieniem komputera docelowego. Jeśli ta zmienna nie jest ustawiona, jest wyświetlany domyślny tekst komunikatu. Określony komunikat nie może przekraczać 512 znaków.<br /><br /> Przykład:<br /><br /> **Zapisz swoją pracę przed ponownym uruchomieniem komputera.**|  
|SMSRebootTimeout<br /><br /> (dane wejściowe)|Określa liczbę sekund wyświetlania ostrzeżenia dla użytkownika przed ponownym uruchomieniem komputera. Określ zero sekund, aby wskazać, że komunikat o ponownym rozruchu nie ma być wyświetlany.<br /><br /> Przykłady:<br /><br /> **0** (ustawienie domyślne)<br /><br />  **60**|  



###  <a name="BKMK_RestoreUserState"></a>Przywróć stan użytkownika   
  Aby uzyskać więcej informacji, zobacz [Przywróć stan użytkownika](task-sequence-steps.md#BKMK_RestoreUserState).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|OSDStateStorePath<br /><br /> (dane wejściowe)|Nazwa ścieżki UNC lub lokalnej dla folderu, z którego jest przywracany stan użytkownika.|  
|OSDMigrateContinueOnRestore<br /><br /> (dane wejściowe)|Kontynuuj proces, nawet w przypadku narzędzia USMT nie można przywrócić niektórych plików.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true,** (ustawienie domyślne)<br /><br /> **wartość false**|  
|OSDMigrateEnableVerboseLogging<br /><br /> (dane wejściowe)|Włącza pełne rejestrowanie dla narzędzia USMT. Ta wartość jest wymagana przez akcję.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDMigrateLocalAccounts<br /><br /> (dane wejściowe)|Określa, czy konto komputera lokalnego jest przywracane.<br /><br /> Prawidłowe wartości:<br /><br /> **wartość true**<br /><br /> **FALSE** (ustawienie domyślne)|  
|OSDMigrateLocalAccountPassword<br /><br /> (dane wejściowe)|Jeśli **zmienna OSDMigrateLocalAccounts** zmienna ma wartość "PRAWDA," Ta zmienna musi zawierać hasło przypisywane do wszystkich migrowanych kont lokalnych. Narzędzie USMT przypisuje to samo hasło do wszystkich migrowanych kont lokalnych. Należy wziąć pod uwagę to hasło jako tymczasowy, a później zmienić za pomocą innej metody.|  
|OSDMigrateAdditionalRestoreOptions<br /><br /> (dane wejściowe)|Określa dodatkowe opcje migracji stanu użytkowników (USMT) Narzędzie wiersza polecenia, które są używane podczas przywracania stanu użytkownika. Dodatkowe opcje są określone w postaci ciągu, który jest dołączany do automatycznie wygenerowanego wiersza polecenia narzędzia USMT. Opcje narzędzia USMT określone za pomocą tej zmiennej sekwencji zadań nie są weryfikowane pod kątem dokładności przed uruchomieniem sekwencji zadań.|  
|_OSDMigrateUsmtRestorePackageID<br /><br /> (dane wejściowe)|Określa identyfikator pakietu pakietu programu Configuration Manager, który zawiera pliki narzędzia USMT. Ta zmienna jest wymagana.|  



###  <a name="BKMK_RunCommand"></a>Uruchom wiersz polecenia   
  Aby uzyskać więcej informacji, zobacz [Uruchom wiersz polecenia](task-sequence-steps.md#BKMK_RunCommandLine).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji|Opis|  
|--------------------------|-----------------|  
|SMSTSDisableWow64Redirection<br /><br /> (dane wejściowe)|Domyślnie na 64-bitowym systemie operacyjnym sekwencja zadań lokalizuje i uruchamia program w wierszu polecenia, za pomocą przekierowania systemu plików WOW64. Takie zachowanie umożliwia polecenie, aby znaleźć 32-bitowe wersje systemu operacyjnego, programów i bibliotek DLL. Ustawienie tej zmiennej **true** wyłącza użycie przekierowania systemu plików WOW64. Polecenie umożliwia znalezienie natywnych 64-bitowych wersjach systemu operacyjnego, programów i bibliotek DLL. Ta zmienna nie ma znaczenia w przypadku uruchomienia w 32-bitowym systemie operacyjnym.|  
|WorkingDirectory<br /><br /> (dane wejściowe)|Określa katalog początkowy dla akcji wiersza polecenia. Nazwa określonego katalogu nie może przekraczać 255 znaków.<br /><br /> Przykłady:<br /><br /> -   **C:\\**<br />-   **%SystemRoot%**|  
|SMSTSRunCommandLineUserName<br /><br /> (dane wejściowe)|Określa konto, za pomocą którego jest uruchamiany wiersz polecenia. Wartość jest ciągiem w formacie nazwa_użytkownika lub domena\nazwa_użytkownika.|  
|SMSTSRunCommandLinePassword<br /><br /> (dane wejściowe)|Określa hasło konta wskazanego przez zmienną SMSTSRunCommandLineUserName.|  



### <a name="set-dynamic-variables"></a>Ustaw zmienne dynamiczne  
Aby uzyskać więcej informacji, zobacz [Ustaw zmienne dynamiczne](task-sequence-steps.md#BKMK_SetDynamicVariables).  

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



###  <a name="BKMK_SetupWindows"></a>Zainstaluj system Windows i program ConfigMgr   
  Aby uzyskać więcej informacji, zobacz [Zainstaluj system Windows i program ConfigMgr](task-sequence-steps.md#BKMK_SetupWindowsandConfigMgr).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|SMSClientInstallProperties<br /><br /> (dane wejściowe)|Określa właściwości instalacji klienta, które są używane podczas instalowania klienta programu Configuration Manager.|  



### <a name="upgrade-operating-system"></a>Uaktualnij system operacyjny  
 Aby uzyskać więcej informacji, zobacz [Uaktualnij System operacyjny](task-sequence-steps.md#BKMK_UpgradeOS).  

#### <a name="details"></a>Szczegóły  

|Nazwa zmiennej akcji<br /><br /> (dane wejściowe)|Opis|  
|----------------------------------------|-----------------|  
|OSDSetupAdditionalUpgradeOptions<br /><br /> (dane wejściowe)|Określa dodatkowe opcje wiersza polecenia, które są dodawane do Instalatora systemu Windows podczas uaktualniania systemu Windows 10. Sekwencja zadań nie weryfikuje opcje wiersza polecenia.<br /><br /> Aby uzyskać więcej informacji, zobacz [opcje wiersza polecenia Instalatora systemu Windows](/windows-hardware/manufacture/desktop/windows-setup-command-line-options).|  
