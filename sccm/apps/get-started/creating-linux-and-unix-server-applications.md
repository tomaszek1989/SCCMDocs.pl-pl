---
title: "Tworzenie aplikacji serwerowych systemów Linux i UNIX"
titleSuffix: Configuration Manager
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla urządzeń z systemem Linux i Unix."
ms.custom: na
ms.date: 04/13/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 79cd131a-1a24-4751-87c8-7f275e45d847
caps.latest.revision: "7"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 81a3ef6ee05a8f0f66ca1a70d56bc33017c66d9c
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="create-linux-and-unix-server-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji serwerowych systemów Linux i UNIX z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas tworzenia i wdrażania aplikacji dla komputerów z systemem Linux i UNIX, należy wziąć pod uwagę następujące kwestie.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 Klient programu Configuration Manager dla systemów Linux i UNIX obsługuje **wdrożenia oprogramowania z wykorzystaniem pakietów i programów**. Nie można wdrożyć aplikacji programu Configuration Manager na komputerach z systemem Linux i UNIX.  

 Możliwości wdrażania oprogramowania w systemach Linux i UNIX obejmują:  

-   Instalacja oprogramowania dla serwerów Linux i UNIX, w tym następujące:  

    -   Nowych wdrożeń oprogramowania  

    -   Aktualizacje oprogramowania dla programów, które znajdują się już na komputerze  

    -   Poprawek systemu operacyjnego  

-   Macierzysty systemu Linux i UNIX polecenia i skryptów, które znajdują się na serwerach Linux i UNIX  

-   Wdrożenia, które są ograniczone do tych systemów operacyjnych określonych w momencie wyboru w programie opcji **tylko na określonych platformach klienckich**

-   Okien obsługi w celu kontrolowania, kiedy oprogramowanie było instalowane

-   Komunikaty o stanie wdrożenia do monitorowania wdrożeń  

-   Opcja dla klienta w celu ograniczania użycia sieci podczas pobierania oprogramowania z punktu dystrybucji  

### <a name="differences-between-deploying-to-linux-and-unix-computers-and-deploying-to-windows-devices"></a>Różnice między wdrażania na komputerach z systemami Linux i UNIX oraz wdrażanie na urządzeniach z systemem Windows
Główne różnice między wdrażaniem pakietów i programów na komputerach z systemami Linux i UNIX oraz wdrażaniem pakietów i programów na urządzeniach z systemem Windows są następujące:  

|Konfiguracja|Szczegóły|  
|-------------------|-------------|  
|Używaj tylko konfiguracji przeznaczonych dla komputerów i nie należy używać konfiguracji przeznaczonych dla użytkowników.|Klient programu Configuration Manager dla systemów Linux i UNIX nie obsługuje konfiguracji przeznaczonych dla użytkowników.|  
|Konfiguruj programy do pobierania oprogramowania z punktu dystrybucji i uruchamiaj je z pamięci podręcznej.|Klient programu Configuration Manager dla systemów Linux i UNIX nie obsługuje uruchamiania oprogramowania z punktu dystrybucji. Zamiast tego należy skonfigurować oprogramowanie do pobierania na klienta, a następnie pobrać.<br /><br /> Domyślnie po instalacji oprogramowania przez klienta systemów Linux i UNIX oprogramowanie to zostaje usunięte z pamięci podręcznej klienta. Niemniej jednak pakiety skonfigurowane przy użyciu opcji **Utrwal zawartość w pamięci podręcznej klienta** nie są usuwane z klienta i pozostają w jego pamięci podręcznej po zainstalowaniu oprogramowania.<br /><br /> Klient dla systemów Linux i UNIX nie obsługuje konfiguracji pamięci podręcznej klienta, a maksymalny rozmiar pamięci podręcznej klienta jest ograniczony tylko ilością wolnego miejsca na dysku komputera klienta.|  
|Skonfiguruj konto dostępu do sieci pod kątem dostępu do punktu dystrybucji|Komputery z systemem Linux i UNIX są przeznaczone do pracy w charakterze komputerów grupy roboczej. Aby uzyskiwać dostęp do pakietów z punktu dystrybucji w domenie serwera lokacji programu Configuration Manager, należy skonfigurować konto dostępu do sieci dla lokacji. Należy określić to konto jako właściwość składnika dystrybucji oprogramowania i skonfigurować je przed wdrożeniem oprogramowania.<br /><br /> W każdej lokacji można skonfigurować wiele kont dostępu do sieci. Klient dla systemów Linux i UNIX może używać każdego z kont skonfigurowanych jako konto dostępu do sieci.<br /><br /> Aby uzyskać więcej informacji, zobacz [Składniki lokacji dla programu System Center Configuration Manager](../../core/servers/deploy/configure/site-components.md).|  

 Pakiety i programy można wdrażać w kolekcjach zawierających tylko klientów systemu Linux lub UNIX albo w kolekcjach zawierających mieszane typy klientów, takich jak kolekcja **Wszystkie systemy**. Klienci z systemem innym niż systemu Linux i UNIX z systemem innym niż nie można jednak zainstalować awarii oprogramowania lub raportu.  

 Gdy klient programu Configuration Manager dla systemów Linux i UNIX otrzymuje i uruchamia wdrożenie, generuje komunikaty o stanie. Te komunikaty o stanie można wyświetlić w konsoli programu Configuration Manager lub za pomocą raportów, aby monitorować stan wdrożenia.  

 Aby uzyskać informacje o sposobie korzystania z pakietów i programów, zobacz [pakiety i programy](../../apps/deploy-use/packages-and-programs.md).  

##  <a name="configure-packages-programs-and-deployments-for-linux-and-unix-servers"></a>Skonfiguruj pakietów, programów i wdrożeń dla serwerów Linux i UNIX  
 Można tworzyć i wdrażać pakiety i programy przy użyciu opcji domyślne dostępne w konsoli programu Configuration Manager. Klient nie wymaga żadnej szczególnej konfiguracji.  

 Informacje zamieszczone w poniższych częściach dotyczą konfigurowania pakietów i programów, a także wdrożeń.  

### <a name="packages-and-programs"></a>Pakiety i programy  
 Aby utworzyć pakiet i program dla serwera z systemem Linux lub UNIX, należy użyć **Kreatora tworzenia pakietu i programu** z konsoli programu Configuration Manager. Klient dla systemów Linux i UNIX obsługuje większość ustawień pakietów i programów. Niektóre ustawienia nie są jednak obsługiwane. Podczas tworzenia lub konfigurowania pakietu i programu należy uwzględnić następujące kwestie:  

-   Dołączenie typów plików, które są obsługiwane przez komputery docelowe.  

-   Zdefiniuj wiersze poleceń, które są odpowiednie do użytku na komputerze docelowym.  

-   Należy pamiętać, że ustawień wymagających interakcji z użytkowników nie są obsługiwane.  

W poniższej tabeli wymieniono właściwości pakietów i programów, które nie są obsługiwane:  

|Właściwość pakietu i programu|Zachowanie|Więcej informacji|  
|----------------------------------|--------------|----------------------|  
|Ustawienia udziału pakietu:<br /><br /> -Wszystkie opcje|Generowany jest błąd i Instalacja oprogramowania kończy się niepowodzeniem.|Klient nie obsługuje tej konfiguracji. Zamiast tego klient musi pobrać oprogramowanie przy użyciu protokołu HTTP lub HTTPS, a następnie uruchomić wiersz polecenia ze swojej lokalnej pamięci podręcznej.|  
|Ustawienia aktualizacji pakietu:<br /><br /> -Odłączania użytkowników od punktów dystrybucji|Ustawienia są ignorowane|Klient nie obsługuje tej konfiguracji.|  
|Ustawienia wdrożenia systemu operacyjnego:<br /><br /> -Wszystkie opcje|Ustawienia są ignorowane|Klient nie obsługuje tej konfiguracji.|  
|Raportowanie:<br /><br /> -Użyj właściwości pakietu do dopasowania pliku MIF stanu<br /><br /> -Użyj tych pól do dopasowania pliku MIF stanu|Ustawienia są ignorowane|Klient nie obsługuje użycia plików MIF stanu.|  
|**Uruchom**:<br /><br /> -Wszystkie opcje|Ustawienia są ignorowane|Klient zawsze uruchamia pakiety bez interfejsu użytkownika.<br /><br /> Klient ignoruje wszystkie opcje konfiguracji polecenia Uruchom.|  
|Po uruchomieniu:<br /><br />-Configuration Manager ponownie uruchomi komputer<br /><br /> — Program kontroluje ponowne uruchomienie<br /><br /> -Menedżer konfiguracji wylogowaniu się użytkownika|Generowany jest błąd i Instalacja oprogramowania kończy się niepowodzeniem.|Ustawienie ponownego uruchamiania systemu i ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Jeśli w użyciu jest jakiekolwiek inne ustawienie niż **Nie są wymagane żadne czynności** , klient generuje błąd i kontynuuje instalację oprogramowania, nie podejmując żadnego działania.|  
|Program może zostać uruchomiony:<br /><br /> -Tylko wtedy, gdy użytkownik jest zalogowany za pomocą|Generowany jest błąd i Instalacja oprogramowania kończy się niepowodzeniem.|Ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Kiedy ta opcja jest skonfigurowana, klient generuje błąd i instalacja oprogramowania kończy się niepowodzeniem.<br /><br /> Inne opcje są ignorowane, a instalacja oprogramowania jest kontynuowana.|  
|Tryb uruchamiania:<br /><br /> -Uruchom z prawami użytkownika|Ustawienia są ignorowane|Ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Klient obsługuje jednak konfigurację uruchamiania z prawami administracyjnymi.<br /><br /> Po określeniu **Uruchom z prawami administracyjnymi**, klienta programu Configuration Manager wykorzystuje swoje poświadczenia główne.<br /><br /> To ustawienie nie generuje błędu ani wpisu dziennika. Zamiast tego Instalacja oprogramowania kończy się niepowodzeniem, kiedy klient generuje błąd dla konfiguracji wymagania wstępnego **Program można uruchomić** = **tylko wtedy, gdy użytkownik jest zalogowany**.|  
|Zezwalaj użytkownikom na wyświetlanie i interakcji z instalacją programu|Ustawienia są ignorowane|Ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Ta konfiguracja jest ignorowana, a instalacja oprogramowania jest kontynuowana.|  
|Tryb dysku:<br /><br /> -Wszystkie opcje|Ustawienia są ignorowane|To ustawienie nie jest obsługiwane, ponieważ zawartość jest zawsze pobierana na klienta i uruchamiana lokalnie.|  
|Uruchom najpierw inny program|Generowany jest błąd i Instalacja oprogramowania kończy się niepowodzeniem.|Cykliczna instalacja programów nie jest obsługiwana.<br /><br /> Kiedy program jest skonfigurowany tak, by najpierw uruchamiał inny program, instalacja oprogramowania kończy się niepowodzeniem, a instalacja innego programu nie rozpoczyna się.|  
|Po przypisaniu tego programu do komputera:<br /><br /> -Uruchom jednokrotnie dla każdego użytkownika, który loguje się|Ustawienia są ignorowane|Ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Klient obsługuje jednak konfigurację uruchamiania raz na komputerze.<br /><br /> To ustawienie nie generuje błędu ani wpisu dziennika, ponieważ błąd i wpis dziennika są już tworzone dla konfiguracji wymagania wstępnego **Program może zostać uruchomiony** = **Tylko, gdy użytkownik jest zalogowany**.|  
|Pomiń powiadomienia programu|Ustawienia są ignorowane|Klient nie implementuje interfejsu użytkownika.<br /><br /> W razie wybrania tej konfiguracji jest ona ignorowana, a instalacja oprogramowania jest kontynuowana.|  
|Wyłącz ten program na komputerach, na których jest wdrożony|Ustawienia są ignorowane|To ustawienie nie jest obsługiwane i nie ma wpływu na instalację oprogramowania.|  
|Zezwalaj na ten program można zainstalować z sekwencji zadań pakietu instalacyjnego bez wdrożenia||Klient nie obsługuje sekwencji zadań.<br /><br /> To ustawienie nie jest obsługiwane i nie ma wpływu na instalację oprogramowania.|  
|Instalator Windows:<br /><br /> -Wszystkie opcje|Ustawienia są ignorowane|Klient nie obsługuje plików ani ustawień Instalatora Windows.|  
|Tryb obsługi programu OpsMgr:<br /><br /> -Wszystkie opcje|Ustawienia są ignorowane|Klient nie obsługuje tej konfiguracji.|  

### <a name="deploy-software-to-a-linux-or-unix-server"></a>Wdrażanie oprogramowania na serwerze z systemem Linux lub UNIX
 Aby wdrożyć oprogramowanie na serwerze Linux lub UNIX za pomocą pakietu i programu, można użyć **Kreatora wdrażania oprogramowania** z konsoli programu Configuration Manager. Większość ustawień wdrażania są obsługiwane przez klienta dla systemów Linux i UNIX. Jednak niektóre ustawienia nie są obsługiwane. Podczas wdrażania oprogramowania, Uwzględnij następujące kwestie:  

-   Pakiet należy zainicjować do obsługi administracyjnej przynajmniej w jednym punkcie dystrybucji, który jest skojarzony z grupą granic skonfigurowaną pod kątem lokalizacji zawartości.  

-   Klient dla systemów Linux i UNIX, który otrzymuje to wdrożenie musi mieć możliwość dostęp do tego punktu dystrybucji ze swojej lokalizacji sieciowej.  

-   Klient dla systemów Linux i UNIX pobiera pakiet z punktu dystrybucji i uruchamia program na komputerze lokalnym.  

-   Klient dla systemów Linux i UNIX nie może pobierać pakietów z folderów udostępnionych. Pobiera on pakiety z punktów dystrybucji z włączoną funkcją usług IIS, obsługujących protokół HTTP lub HTTPS.  

 Nieobsługiwane właściwości wdrożeń przedstawiono w poniższej tabeli.  

|Właściwość wdrożenia|Zachowanie|Więcej informacji|  
|-------------------------|--------------|----------------------|  
|Ustawienia wdrożenia — cel:<br /><br /> -Dostępne<br /><br /> -Wymagane|Ustawienia są ignorowane|Ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Klient obsługuje jednak ustawienie **Wymagane**, które egzekwuje zaplanowany czas instalacji, choć nie obsługuje instalacji ręcznej przed tym zaplanowanym czasem.|  
|Wyślij pakiety wzbudzania|Ustawienia są ignorowane|Klient nie obsługuje tej konfiguracji.|  
|Harmonogram przypisania:<br /><br /> -logowania<br /><br /> -wylogowania|Generowany jest błąd i Instalacja oprogramowania kończy się niepowodzeniem.|Ustawienia specyficzne dla użytkownika nie są obsługiwane.<br /><br /> Klient obsługuje jednak ustawienie **Najszybciej, jak to możliwe**.|  
|Ustawienia powiadomień:<br /><br /> -Zezwalaj użytkownikom na uruchamianie programu niezależnie od przypisań|Ustawienia są ignorowane|Klient nie implementuje interfejsu użytkownika.|  
|Po osiągnięciu zaplanowanego czasu przypisania zezwalaj na wykonywanie następujących czynności poza oknem obsługi:<br /><br /> -Ponowne uruchomienie systemu (Jeśli wymagane w celu ukończenia instalacji)|Zostaje wygenerowany błąd|Klient nie obsługuje ponownego uruchamiania systemu.|  
|Opcja wdrażania dla szybkich sieci (LAN):<br /><br /> -Uruchom program z punktu dystrybucji|Generowany jest błąd i Instalacja oprogramowania kończy się niepowodzeniem.|Klient nie może uruchamiać oprogramowania z punktu dystrybucji, tylko musi pobrać program, aby móc go uruchomić.|  
|Opcja wdrażania w granicach wolnej lub zawodnej sieci albo dla rezerwowej lokalizacji źródła zawartości:<br /><br /> -Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci|Ustawienia są ignorowane|Klient nie obsługuje udostępniania zawartości między komputerami równorzędnymi.|  

 Aby uzyskać więcej informacji o lokalizacji zawartości, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 Aby uzyskać więcej informacji o sposobach tworzenia wdrożenia, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).  

##  <a name="manage-network-bandwidth-for-software-downloads-from-distribution-points"></a>Zarządzanie przepustowością sieci dla modułu pobierania oprogramowania z punktów dystrybucji  
 Klient systemu Linux i UNIX obsługuje kontrolę przepustowości sieci podczas pobierania oprogramowania z punktu dystrybucji.  

 Klient korzysta z ustawień Background Intelligent Transfer (BITS), które można skonfigurować jako ustawienia klienta w programie Configuration Manager, ale nie implementuje usługi BITS. Zamiast tego, aby ograniczać wykorzystanie przepustowości sieci, klient kontroluje dla pobierania oprogramowania rozmiar fragmentów żądań HTTP i opóźnienie między fragmentami.  

 Aby skonfigurować dla klienta użycie kontroli przepustowości sieci, należy skonfigurować ustawienia klienta dla usługi **Inteligentnego transferu w tle** , a następnie zastosować je na komputerze klienta. W celu używania kontroli przepustowości klient musi odebrać ustawienia klienta dla **inteligentnego transferu w tle** z następującymi ustawieniami skonfigurowany jako **tak**:  

-   **Ogranicz maksymalną przepustowość sieci dla transferów w tle wykonywanych przez usługę BITS**  

 Klient obsługuje następujące konfiguracje Inteligentnego transferu w tle:  

    -   **Godzina rozpoczęcia okna ograniczenia przepustowości**  

    -   **Godzina zakończenia okna ograniczenia przepustowości**  

    -   **Maksymalna szybkość transferu w oknie ograniczenia przepustowości (Kb/s)**  

    -   **Maksymalna szybkość transferu poza oknem ograniczenia przepustowości (Kb/s)**  

Następująca konfiguracja usługi inteligentnego transferu w tle nie jest obsługiwana, jest więc ignorowana przez klienta dla systemów Linux i UNIX:  

-   **Zezwalaj na pobieranie usługi BITS poza oknem ograniczenia przepustowości**  

 Jeśli pobieranie oprogramowania klienta z punktu dystrybucji zostanie przerwane, klient dla systemów Linux i UNIX nie wznawia pobierania. Zamiast tego ponownie uruchamia pobieranie całego pakietu oprogramowania.  

##  <a name="configure-operations-for-software-deployments"></a>Skonfiguruj operacje dotyczące wdrożeń oprogramowania  
 Podobnie jak klient systemu Windows, klient programu Configuration Manager dla systemów Linux i UNIX odnajduje nowe wdrożenia oprogramowania kiedy sonduje i sprawdza, czy nowe zasady. Częstotliwość, z którą klient sprawdza, czy nie występują nowe zasady, zależy od ustawień klienta. W celu kontrolowania, kiedy oprogramowanie zostanie zainstalowane, można konfigurować okna obsługi.  

 Wdrażanie oprogramowania na serwerach z systemem Linux i UNIX można konfigurować za pomocą właściwości: pakietów, programów i wdrożeń.  

 Kiedy klient otrzymuje zasady dla jakiegoś wdrożenia, przesyła komunikat o stanie. Przesyła również komunikaty o stanie, podczas uruchamiania instalacji oprogramowania i podczas instalacji zakończenie lub kończy się niepowodzeniem.  

 Programy do wdrażania oprogramowania są uruchamiane z poświadczeniami głównymi, które jest uruchamiany klient programu Configuration Manager dla systemów Linux i UNIX. Do ustalenia powodzenia lub niepowodzenia służy kod zakończenia polecenia programów. Za powodzenie uznaje się kod zakończenia wynoszący 0 (zero). Ponadto, kiedy poziom dziennika zostanie ustawiony na INFO albo TRACE, do pliku dziennika są kopiowane parametry **stdout** (standardowy strumień wyjściowy) i **stderr** (standardowy strumień błędów).  

> [!TIP]  
>  Jeśli oprogramowanie do wdrożenia znajduje się w udziale systemu plików Network File System (NFS), do którego ma dostęp serwer z systemem Linux lub UNIX, nie musisz w celu pobrania pakietu korzystać z punktu dystrybucji. Zamiast tego podczas tworzenia pakietu nie zaznaczaj pola wyboru opcji **Ten pakiet zawiera pliki źródłowe**. Następnie podczas konfiguracji programu określ odpowiedni wiersz polecenia, aby uzyskać bezpośredni dostęp do pakietu w punkcie instalacji NFS.  
