---
title: "Zarządzanie ustawieniami aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o ustawieniach klienta, które są odpowiednie dla aktualizacji oprogramowania w lokacji po zainstalowaniu punktu aktualizacji oprogramowania."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 03/26/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 0d484c1a-e903-4bff-9e9b-e452c62e38a8
ms.openlocfilehash: fe4a8f56e0b554e206bcc4503a0268dc761ded81
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
#  <a name="BKMK_ManageSUSettings"></a>Zarządzanie ustawieniami aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po zsynchronizowaniu aktualizacji oprogramowania w programie Configuration Manager, skonfiguruj i sprawdź ustawienia w poniższych sekcjach.

##  <a name="BKMK_ClientSettings"></a> Ustawienia klienta dotyczące aktualizacji oprogramowania  
Po zainstalowaniu punktu aktualizacji oprogramowania aktualizacje te są domyślnie włączone na klientach, a ustawienia na stronie **Aktualizacje oprogramowania** mają przypisane wartości domyślne. Ustawienia klienta są używane w całej lokacji oraz mają wpływ, jeśli aktualizacje oprogramowania są skanowane pod kątem zgodności, a następnie, kiedy aktualizacje oprogramowania są zainstalowane na komputerach klienckich. Przed wdrożeniem aktualizacji oprogramowania, sprawdź, czy ustawienia klienta są odpowiednie dla aktualizacji oprogramowania w danej lokacji.  

> [!IMPORTANT]  
>  Ustawienie **Włącz aktualizacje oprogramowania na klientach** jest domyślnie włączone. Jeśli wyczyścisz to ustawienie, programu Configuration Manager usunie istniejące zasady wdrażania z klienta.  

Aby uzyskać informacje o sposobie konfigurowania ustawień klienta, zobacz [sposób konfigurowania ustawień klienta](../../core/clients/deploy/configure-client-settings.md).  

Aby uzyskać więcej informacji o ustawieniach klienta, zobacz [informacje o ustawieniach klienta](../../core/clients/deploy/about-client-settings.md).  

##  <a name="BKMK_GroupPolicy"></a> Ustawienia zasad grupy dotyczące aktualizacji oprogramowania  
Zasady grupy zawierają konkretne ustawienia, które są używane przez usługę Windows Update Agent (WUA) na komputerach klienckich do łączenia się z serwerem WSUS uruchomionym w punkcie aktualizacji oprogramowania. Te ustawienia zasad grupy są również używane do skanowania pod kątem zgodności aktualizacji oprogramowania oraz do automatycznego aktualizowania aktualizacji oprogramowania oraz usługi WUA.

### <a name="specify-intranet-microsoft-update-service-location-local-policy"></a>Lokalne zasady Określ lokalizację intranetowej usługi aktualizującej firmy Microsoft  
Jeśli dla lokacji utworzono punkt aktualizacji oprogramowania, klienci odbierają zasady komputera dostarczające nazwę serwera punktu aktualizacji oprogramowania i konfigurującą na komputerze zasady lokalne **Określ lokalizację intranetową usługi aktualizującej firmy Microsoft** . Usługa WUA pobiera nazwę serwera określoną w ustawieniu **Ustaw intranetową usługę aktualizującą do wykrywania aktualizacji** , a następnie łączy się z tym serwerem podczas skanowania pod kątem zgodności aktualizacji oprogramowania. Jeśli dla ustawienia **Określ lokalizację intranetową usługi aktualizującej firmy Microsoft** zostaną utworzone zasady domeny, zastąpią one zasady lokalne. Wtedy usługa WUA może nawiązywać połączenie z serwerem innym niż punkt aktualizacji oprogramowania. Gdy tak się stanie, klient może skanować zgodność aktualizacji oprogramowania na podstawie innych produktów, klasyfikacji i języków. W związku z tym nie należy konfigurować zasady usługi Active Directory dla komputerów klienckich.  

### <a name="allow-signed-content-from-intranet-microsoft-update-service-location-group-policy"></a>Zasady grupy Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft  
Ustawienie zasad grupy **Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft** należy włączyć, zanim usługa WUA na komputerach rozpocznie skanowanie aktualizacji oprogramowania utworzonych i opublikowanych przez program System Center Updates Publisher. Gdy to ustawienie zasad jest włączone, usługa WUA będzie akceptować aktualizacje oprogramowania odbierane za pośrednictwem lokalizacji intranetowej, jeśli będą one podpisane w magazynie certyfikatów **Zaufani wydawcy** na komputerze lokalnym. Więcej informacji o ustawieniach zasad grupy, które są wymagane przez program Updates Publisher, zawiera [Biblioteka dokumentacji programu Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=232476).  

### <a name="automatic-updates-configuration"></a>Konfigurowanie aktualizacji automatycznych  
Aktualizacje automatyczne umożliwiają odbieranie aktualizacji zabezpieczeń i innych ważnych pobieranych treści na komputerach klienckich. Aktualizacje automatyczne są konfigurowane za pomocą ustawienia **Konfigurowanie aktualizacji automatycznych** zasad grupy lub za pomocą Panelu sterowania na komputerze lokalnym. Jeśli aktualizacje automatyczne są włączone, komputery klienckie odbierają powiadomienia o aktualizacji, a następnie pobierają i instalują wymagane aktualizacje zgodnie ze skonfigurowanymi ustawieniami. Jeśli aktualizacje automatyczne są używane razem z aktualizacjami oprogramowania, na każdym komputerze klienckim mogą być wyświetlane okna podręczne oraz ikony powiadomień dotyczące tej samej aktualizacji. Ponadto, jeśli jest wymagane ponowne uruchomienie, każdy komputer kliencki może wyświetlać okno dialogowe ponownego uruchomienia dotyczące tej samej aktualizacji.  

### <a name="self-update"></a>Samoaktualizacje  
Gdy na komputerach klienckich są włączone aktualizacje automatyczne, usługa WUA automatycznie wykonuje samoaktualizacje, gdy stanie się dostępna nowsza wersja lub gdy występują problemy ze składnikiem usługi WUA. Jeśli aktualizacje automatyczne nie są skonfigurowane lub są wyłączone, a na komputerach klienckich jest zainstalowana starsza wersja usługi WUA, należy na nich uruchomić plik instalacyjny usługi WUA.  

## <a name="software-updates-properties"></a>Właściwości aktualizacji oprogramowania
Właściwości aktualizacji oprogramowania zawierają informacje o aktualizacjach oprogramowania i powiązanej z nimi zawartości. Można również użyć ich do skonfigurowania ustawień aktualizacji oprogramowania. W oknie właściwości wielu aktualizacji oprogramowania będą wyświetlane jedynie karty **Maksymalny czas działania** oraz **Ważność niestandardowa** .   

Aby otworzyć okno właściwości aktualizacji oprogramowania, wykonaj następującą procedurę.  

#### <a name="to-open-software-update-properties"></a>Aby otworzyć okno właściwości aktualizacji oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  
2.  W obszarze roboczym Biblioteka oprogramowania rozwiń listę **Aktualizacje oprogramowania**, a następnie kliknij pozycję **Wszystkie aktualizacje oprogramowania**.  
3.  Wybierz co najmniej jedną aktualizację oprogramowania, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości** .  

   > [!NOTE]  
   >  Na **wszystkie aktualizacje oprogramowania** węzła, programu Configuration Manager wyświetla wyłącznie aktualizacje oprogramowania, które mają **krytyczny** i **zabezpieczeń** klasyfikacji i które zostały wydane w ciągu ostatnich 30 dni.  

###  <a name="BKMK_SoftwareUpdatesInformation"></a> Przeglądanie informacji o aktualizacjach oprogramowania  
W oknie właściwości oprogramowania można wyświetlić szczegółowe informacje o aktualizacji oprogramowania. Szczegółowe informacje nie będą wyświetlane w przypadku wybrania więcej niż jednej aktualizacji oprogramowania. Następujące sekcje opisują informacje dostępne dla wybranej aktualizacji oprogramowania.  

####  <a name="BKMK_SoftwareUpdateDetails"></a> Szczegóły aktualizacji oprogramowania  
Na karcie **Szczegóły aktualizacji** można wyświetlić następujące podsumowanie informacji na temat wybranej aktualizacji oprogramowania:  

- **Identyfikator biuletynu**: Określa identyfikator biuletynu skojarzony z aktualizacjami oprogramowania zabezpieczeń. Szczegółowe informacje o biuletynie zabezpieczeń można znaleźć, wyszukując identyfikator biuletynu w witrynie internetowej [Microsoft Security Bulletin Search](http://go.microsoft.com/fwlink/p/?LinkId=58313) .  

- **Identyfikator artykułu**: Określa identyfikator artykułu dotyczącego aktualizacji oprogramowania. Ów artykuł zawiera bardziej szczegółowe informacje na temat aktualizacji oprogramowania i wersji, której poprawkę lub udoskonalenie stanowi dana aktualizacja.  

- **Data zmian**: Określa datę ostatniej modyfikacji aktualizacji oprogramowania.  

- **Maksymalna ocena ważności**: Określa zdefiniowaną przez dostawcę ważności dla aktualizacji oprogramowania.  

- **Opis elementu**: Zawiera omówienie stanu aktualizacji oprogramowania, którego poprawkę lub udoskonalenie stanowi.  

- **Właściwe języki**: Wyświetla listę języków, których dotyczy dana aktualizacja oprogramowania.  

- **Objęte produkty**: Zawiera listę produktów, których dotyczy dana aktualizacja oprogramowania.  

####  <a name="BKMK_ContentInformation"></a> Informacje o zawartości  
Na karcie **Informacje o zawartości** przejrzyj następujące informacje dotyczące zawartości powiązanej z wybraną aktualizacją oprogramowania:  

-   **Identyfikator zawartości**: Określa identyfikator zawartości aktualizacji oprogramowania.  

-   **Pobrane**: Wskazuje, czy programu Configuration Manager pobrał pliki aktualizacji oprogramowania.  

-   **Język**: Określa języki aktualizacji oprogramowania.  

-   **Ścieżka źródłowa**: Określa ścieżkę do plików źródłowych aktualizacji oprogramowania.  

-   **Rozmiar (MB)**: Określa rozmiar plików źródłowych aktualizacji oprogramowania.  

####  <a name="BKMK_CustomBundleInformation"></a> Informacje o pakiecie niestandardowym  
Na karcie **Informacje o pakiecie niestandardowym** przejrzyj informacje o pakiecie niestandardowym aktualizacji oprogramowania. Jeśli wybrana aktualizacja oprogramowania zawiera powiązane aktualizacje oprogramowania w jednym pliku aktualizacji, zostaną one wyświetlone w sekcji **Informacje o pakiecie** . Na tej karcie nie będą wyświetlane powiązane aktualizacje oprogramowania wyświetlane na karcie **Informacje o zawartości** , takie jak pliki aktualizacji dla różnych języków.  

####  <a name="BKMK_SupersedenceInformation"></a> Informacje o zastępowaniu  
Na karcie **Informacje o zastępowaniu** można wyświetlić następujące informacje dotyczące zastępowania aktualizacji oprogramowania:  

- **Ta aktualizacja została zastąpiona następującymi aktualizacjami**: Określa aktualizacje oprogramowania zastępujące daną aktualizację, co oznacza, że wymienione aktualizacje są nowsze. W większości przypadków zostanie wdrożona jedna z aktualizacji oprogramowania zastępujących daną aktualizację. Aktualizacje oprogramowania wyświetlane na liście zawierają hiperłącza do witryn internetowych, w których można znaleźć więcej informacji na temat tych aktualizacji. Jeśli aktualizacja nie jest zastępowana przez żadną inną aktualizację, zostanie wyświetlona wartość **Brak** .  

- **Ta aktualizacja zastępuje następujące aktualizacje**: Określa aktualizacje oprogramowania, które są zastępowane przez tę aktualizację oprogramowania, co oznacza, że ta aktualizacja oprogramowania jest nowsza. W większości przypadków ta aktualizacja oprogramowania zostanie wdrożona w celu zastąpienia starszych aktualizacji oprogramowania. Aktualizacje oprogramowania wyświetlane na liście zawierają hiperłącza do witryn internetowych, w których można znaleźć więcej informacji na temat tych aktualizacji. Jeśli ta aktualizacja nie zastępuje żadnej innej aktualizacji, zostanie wyświetlona wartość **Brak** .  

###  <a name="BKMK_SoftwareUpdatesSettings"></a> Konfigurowanie ustawień aktualizacji oprogramowania  
W oknie właściwości można skonfigurować ustawienia aktualizacji oprogramowania dotyczące co najmniej jednej aktualizacji. Większość ustawień aktualizacji oprogramowania można skonfigurować wyłącznie w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Następujące sekcje zawierają informacje pomocne podczas konfigurowania ustawień aktualizacji oprogramowania.  

####  <a name="BKMK_SetMaxRunTime"></a> Ustawianie maksymalnego czasu działania  
Na karcie **Maksymalny czas działania** ustaw maksymalny czas działania przydzielony aktualizacji oprogramowania na komputerach klienckich. Jeśli aktualizacja trwa dłużej niż maksymalny wyznaczony czas działania, Configuration Manager utworzy komunikat o stanie i przestanie monitorować wdrożenie instalacji aktualizacji oprogramowania. To ustawienie można skonfigurować wyłącznie w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

Configuration Manager używa również to ustawienie, aby określić, czy należy zainicjować instalację aktualizacji oprogramowania w ramach skonfigurowanego okna obsługi. Jeśli wartość maksymalnego czasu działania jest większa niż wartość dostępnego czasu w oknie obsługi, instalacja aktualizacji oprogramowania zostanie odłożona do momentu rozpoczęcia następnego okna obsługi. Jeśli na komputerze klienckim ze skonfigurowanym oknem obsługi (ramami czasowymi) należy zainstalować wiele aktualizacji oprogramowania, w pierwszej kolejności zostanie zainstalowana aktualizacja o najkrótszym maksymalnym czasie działania, następnie aktualizacja o drugim najkrótszym maksymalnym czasie działania i tak dalej. Przed zainstalowaniem każdej aktualizacji oprogramowania klient sprawdzi, czy dostępne okno obsługi zapewni odpowiednią ilość czasu na zainstalowanie aktualizacji obsługi. Rozpoczęta instalacja aktualizacja obsługi będzie kontynuowana również w przypadku, gdy jej czas będzie wykraczał poza czas okna obsługi. Aby uzyskać więcej informacji o korzystaniu z okien obsługi, zobacz [Używanie okien obsługi w programie System Center Configuration Manager](../../core/clients/manage/collections/use-maintenance-windows.md).  

Na karcie **Maksymalny czas działania** można wyświetlić i skonfigurować następujące ustawienia:  

- **Maksymalny czas wykonywania**: Określa maksymalną liczbę minut wyznaczoną na ukończenie instalacji jest już monitorowany przez program Configuration Manager instalacji aktualizacji oprogramowania. To ustawienie umożliwia również określenie, czy czas pozostały do zakończenia okna obsługi jest wystarczający, aby zainstalować aktualizację. Domyślne ustawienie to 60 minut dla dodatków service pack. Dla innych typów aktualizacji oprogramowania wartość domyślna to 10 minut, jeśli została ona nowej instalacji programu Configuration Manager w wersji 1511 lub nowszej i 5 minut po uaktualnieniu z poprzedniej wersji. Dopuszczalny zakres wartości wynosi od 5 do 9999 minut.  

> [!IMPORTANT]  
>  Należy pamiętać, aby wartość maksymalnego czasu działania była mniejsza od wartości czasu skonfigurowanego okna obsługi. W przeciwnym razie instalacja aktualizacji oprogramowania nie zostanie nigdy zainicjowana.  

####  <a name="BKMK_SetCustomSeverity"></a> Ustawianie ważności niestandardowej  
We właściwościach aktualizacji oprogramowania na karcie **Ważność niestandardowa** można skonfigurować niestandardowe wartości ważności aktualizacji oprogramowania. Może to być konieczne, gdy wstępnie zdefiniowane wartości ważności nie spełniają potrzeb użytkownika. Wartości niestandardowe są wymienione w **ważność niestandardowa** kolumny w konsoli programu Configuration Manager. Aktualizacje oprogramowania można sortować wg zdefiniowanych wartości niestandardowych ważności, a także tworzyć kwerendy i raporty w celu filtrowania tych wartości. To ustawienie można skonfigurować wyłącznie w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

Na karcie **Ważność niestandardowa** można skonfigurować następujące ustawienia:  

- **Ważność niestandardowa**: Ustawia niestandardowej wartości ważności aktualizacji oprogramowania. Wybierz z listy opcję **Krytyczne**, **Ważne**, **Umiarkowane**lub **Niska** . Domyślnie pole niestandardowej wartości ważności jest puste.

## <a name="crl-checking-for-software-updates"></a>Sprawdzanie listy CRL dla aktualizacji oprogramowania
Domyślnie listy odwołania certyfikatów (CRL) nie jest sprawdzana podczas weryfikowania podpisu aktualizacji oprogramowania System Center Configuration Manager. Sprawdzanie listy CRL przy każdorazowym użyciu certyfikatu zapewnia lepszą ochronę przed potencjalnym użyciem odwołanego certyfikatu, jednak wprowadza opóźnienie komunikacji i konieczność dodatkowego przetwarzania danych na komputerze wykonującym weryfikację listy.  

Jeśli używana, sprawdzanie listy CRL musi być włączona konsol programu Configuration Manager, które przetwarzają aktualizacje oprogramowania.  

#### <a name="to-enable-crl-checking"></a>Aby włączyć sprawdzanie listy CRL  
Na komputerze wykonującym sprawdzanie listy CRL z dysku DVD produktu uruchom następujące polecenie w wierszu polecenia: **\SMSSETUP\BIN\X64\\**<*języka*>**\UpdDwnldCfg.exe /checkrevocation**.  

Na przykład dla języka angielskiego (US) uruchom **\SMSSETUP\BIN\X64\00000409\UpdDwnldCfg.exe /checkrevocation**  
