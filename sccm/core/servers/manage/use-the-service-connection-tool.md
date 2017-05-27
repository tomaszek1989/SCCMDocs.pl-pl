---
title: "Narzędzie połączenia usługi | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat tego narzędzia, który umożliwia połączenia z usługą w chmurze programu Configuration Manager ręcznie przekazać informacje o wykorzystaniu."
ms.custom: na
ms.date: 4/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6e4964c5-43cb-4372-9a89-b62ae6a4775c
caps.latest.revision: 11
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 32f7fc4ef9c8e8d3c2ec8eeaf9a3174bad992ffb
ms.openlocfilehash: 0da80521bf223a765c3731f8ad59623d85a4c9fa
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-the-service-connection-tool-for-system-center-configuration-manager"></a>Używanie narzędzia połączenia z usługą w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj **narzędzia połączenia usługi** gdy ten punkt połączenia usługi jest w trybie offline lub gdy serwerów systemu lokacji programu Configuration Manager nie są połączone z Internetem. Narzędzie może pomóc aktualności lokacji przy użyciu najnowszych aktualizacji programu Configuration Manager.  

W czasie wykonywania narzędzie ręcznie łączy się z usługą w chmurze programu Configuration Manager do przekazywania informacji o użyciu dla hierarchii i pobierania aktualizacji. Przekazywanie danych o użyciu jest niezbędne, aby usługa w chmurze mogła dostarczyć prawidłowe aktualizacje do wdrożenia.  

## <a name="prerequisites-for-using-the-service-connection-tool"></a>Wymagania wstępne dotyczące korzystania z narzędzia połączenia usługi
Poniżej przedstawiono wymagania wstępne i znanych problemów.

**Wymagania wstępne:**

-   Masz zainstalowany punkt połączenia z usługą, który jest ustawiony na opcję **Offline, połączenie na żądanie**.  

-   Narzędzie musi być uruchamiane z wiersza polecenia.  

-   Każdy komputer, na którym działa narzędzie (komputer z punktem połączenia z usługą i komputer połączony z Internetem) musi być systemem 64-bitowym, a na komputerze musi być zainstalowane następujące oprogramowanie:  

    -   Pliki **pakietu redystrybucyjnego Visual C++** w wersji x86 i x64.   Domyślnie program Configuration Manager instaluje x64 wersji na komputerze, który jest hostem punktu połączenia usługi.  

         Aby pobrać kopię plików Visual C++, odwiedź stronę [Visual C++ Redistributable Packages for Visual Studio 2013](http://www.microsoft.com/download/details.aspx?id=40784) (Pakiety redystrybucyjne Visual C++ dla programu Visual Studio 2013) w Centrum pobierania Microsoft.  

    -   .NET Framework w wersji 4.5.2 lub nowszej.  

-   Konto używane do uruchamiania narzędzia musi mieć:
    -   Uprawnienia**Administrator lokalny** na komputerze, który jest hostem punktu połączenia usługi (na którym narzędzie jest uruchamiane).
    -   Uprawnienia**Odczyt** do bazy danych lokacji.  



-   Potrzebny będzie dysk USB z wystarczającą ilością wolnego miejsca do przechowywania plików i aktualizacji lub znalezienie innej metody transferu plików między komputerem punktu połączenia z usługą i komputerem mającym dostęp do Internetu. (W tym scenariuszu przyjęto, że ani lokacja, ani komputery zarządzane nie mają bezpośredniego połączenia z Internetem).  



## <a name="use-the-service-connection-tool"></a>Używanie narzędzia połączenia usługi  

 Narzędzie połączenia usługi można znaleźć (**serviceconnectiontool.exe**), na nośniku instalacyjnym programu Configuration Manager w **%path%\smssetup\tools\ServiceConnectionTool** folder. Zawsze używaj narzędzia połączenia usługi, która jest zgodna z wersją programu Configuration Manager można użyć.


 W tej procedurze w przykładach dotyczących wiersza polecenia używane są następujące nazwy plików i lokalizacje folderów (są to przykładowe ścieżki i nazwy plików, które można zamienić na odpowiednie dla swojego środowiska i swoich preferencji):  

-   Ścieżka do manipulatora USB, w którym są przechowywane dane w ramach transferu między serwerami:  **D:\USB\\**  

-   Nazwa pliku .cab, który zawiera dane wyeksportowane z witryny: **UsageData.cab**  

-   Nazwa pusty folder, w którym będą przechowywane pobrane aktualizacje programu Configuration Manager w ramach transferu między serwerami: **UpdatePacks**  

Na komputerze hostującym punkt połączenia z usługą:  

-   Otwórz wiersz polecenia z uprawnieniami administracyjnymi, a następnie przejdź do lokalizacji zawierającej plik **serviceconnectiontool.exe**.  

     Domyślnie to narzędzie można znaleźć na nośniku instalacyjnym programu Configuration Manager w **%path%\smssetup\tools\ServiceConnectionTool** folder. Aby narzędzie połączenia z usługą zadziałało, wszystkie pliki z tego folderu muszą znajdować się w jednym folderze.  

Po uruchomieniu poniższego polecenia narzędzie przygotowuje plik cab, który zawiera informacje dotyczące użycia, i kopiuje go do określonej lokalizacji. Dane w pliku cab są uzależnione od skonfigurowanego poziomu danych diagnostycznych i danych użycia zbieranych przez lokację. (zobacz [Dane diagnostyczne i dane użycia dla programu System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md)).  Uruchom następujące polecenie, aby utworzyć plik cab:  

-   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

Musisz także skopiować folder ServiceConnectionTool wraz z całą zawartością na dysk USB lub w inny sposób udostępnić go na komputerze, na którym zostaną wykonane kroki 3 i 4.  

### <a name="overview"></a>Omówienie
**Aby użyć narzędzia połączenia z usługą, należy wykonać trzy podstawowe kroki:**  

1.  **Przygotuj**:  Ten krok działa na komputerze, który jest hostem punktu połączenia usługi. Po uruchomieniu narzędzia umieszcza dane użycia w pliku cab i zapisze go na dysku USB lub określ transferu alternatywnej lokalizacji.  

2.  **Połącz**: W tym kroku uruchom narzędzie na komputerze zdalnym, który łączy się z Internetem, aby można było przekazać dane użycia i następnie pobrać aktualizacje.  

3.  **Importuj**: Ten krok działa na komputerze, który jest hostem punktu połączenia usługi. W czasie wykonywania narzędzie można pobrać importuje i dodaje je do lokacji, można wyświetlić i zainstalować te aktualizacje z konsoli programu Configuration Manager.  

Począwszy od wersji 1606, podczas nawiązywania połączenia z firmą Microsoft można przekazać wiele plików cab jednocześnie (każdy z innej hierarchii), a także określić serwer proxy i użytkownika serwera proxy.   

**Aby przekazać wiele plików cab:**
 -  Umieść każdy plik cab wyeksportowany z oddzielnych hierarchii w tym samym folderze. Nazwa każdego pliku musi być unikatowa i można ją zmienić ręcznie, jeśli to konieczne.
 -  Następnie po uruchomieniu polecenia przekazywania danych do firmy Microsoft określ folder, w którym znajdują się pliki cab. Przed aktualizacją 1606 dane można było przekazywać tylko z jednej hierarchii jednocześnie, a narzędzie wymagało, aby określić nazwę pliku cab w folderze.
 -  Następnie podczas uruchamiania zadania importu w punkcie połączenia usługi hierarchii narzędzie automatycznie importuje tylko dane dla tej hierarchii.  

**Aby określić serwer proxy:**  
Aby określić serwer proxy, można użyć następujących parametrów opcjonalnych (więcej informacji dotyczących używania tych parametrów jest dostępnych w sekcji Parametry wiersza polecenia w tym temacie):
  - **-proxyserveruri [nazwa_FQDN_serwera_proxy]**  Użyj tego parametru, aby określić serwer proxy, który zostanie użyty na potrzeby tego połączenia.
  -  **-proxyusername [nazwa_użytkownika]**  Użyj tego parametru w przypadku konieczności określenia użytkownika serwera proxy.



### <a name="to-use-the-service-connection-tool"></a>Aby użyć narzędzia połączenia z usługą  

1.  Na komputerze hostującym punkt połączenia z usługą:  

    -   Otwórz wiersz polecenia z uprawnieniami administracyjnymi, a następnie przejdź do lokalizacji zawierającej plik **serviceconnectiontool.exe**.   

2.  Uruchom poniższe polecenie w celu przygotowania przez narzędzie pliku cab, który zawiera informacje dotyczące użycia, i skopiowania go do określonej lokalizacji:  

    -   **serviceconnectiontool.exe -prepare -usagedatadest D:\USB\UsageData.cab**  

    Jeśli będą przekazywane pliki cab z więcej niż jednej hierarchii jednocześnie, każdy plik cab w folderze musi mieć unikatową nazwę. Nazwy plików dodawanych do folderów można zmieniać ręcznie.

    Jeśli chcesz przejrzeć informacje o użyciu przygotowane do przesłania do usługi Configuration Manager w chmurze, uruchom poniższe polecenie, aby wyeksportować te dane do pliku csv, który następnie można otworzyć np. w programie Excel:  

    -   **serviceconnectiontool.exe -export -dest D:\USB\UsageData.csv**  

3.  Po ukończeniu kroku przygotowawczego podłącz dysk USB (lub prześlij wyeksportowane dane przy użyciu innej metody) do komputera mającego dostęp do Internetu.  

4.  Na komputerze z dostępem do Internetu otwórz wiersz polecenia z uprawnieniami administracyjnymi, a następnie przejdź do lokalizacji zawierającej kopię narzędzia  **serviceconnectiontool.exe** i dodatkowe pliki z tego folderu.  

5.  Uruchom następujące polecenie, aby rozpocząć przesyłanie informacji o użyciu i pobieranie aktualizacji programu Configuration Manager:  

    -   **serviceconnectiontool.exe-Połącz D:\USB\UpdatePacks - updatepackdest D:\USB - usagedatasrc**

    Więcej przykładów tego wiersza polecenia znajduje się w sekcji [Opcje wiersza polecenia](../../../core/servers/manage/use-the-service-connection-tool.md#bkmk_cmd) w dalszej części tego tematu.

    > [!NOTE]  
    >  Po uruchomieniu wiersza polecenia, aby połączyć się z usługą Configuration Manager w chmurze, może wystąpić błąd podobny do następującego:  
    >   
    >  -   Nieobsługiwany wyjątek: System.UnauthorizedAccessException:  
    >   
    >      Odmowa dostępu do ścieżki „C:\  
    >     Users\br\AppData\Local\Temp\extractmanifestcab\95F8A562.sql”.  
    >   
    > Można bezpiecznie zignorować ten błąd, zamknąć okno i kontynuować pracę.  

6.  Po zakończeniu pobierania aktualizacji dla programu Configuration Manager przenieś dysk USB (lub przenieś wyeksportowane dane przy użyciu innej metody) do komputera, który hostuje punkt połączenia z usługą.  

7.  Na komputerze, który jest hostem punktu połączenia z usługą, otwórz wiersz polecenia z uprawnieniami administracyjnymi, przejdź do lokalizacji zawierającej plik **serviceconnectiontool.exe**i uruchom następujące polecenie:  

    -   **serviceconnectiontool.exe -import -updatepacksrc D:\USB\UpdatePacks**  

8.  Po zakończeniu importowania możesz zamknąć wiersz polecenia. (Importowane są tylko aktualizacje dla odpowiednich hierarchii).  

9. Otwórz konsolę programu Configuration Manager i przejdź do **Administracja** > **aktualizacji i obsługi**. Aktualizacje, które zostały zaimportowane, są teraz dostępne do zainstalowania. (Przed wersją 1702, aktualizacji i obsługi został pod **Administracja** > **usług w chmurze**.)

 Aby uzyskać informacje o instalowaniu aktualizacji, zobacz [Instalacja aktualizacji w konsoli programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md).  

## <a name="bkmk_cmd"></a> Opcje wiersza polecenia  
 Aby wyświetlić informacje pomocnicze o narzędziu punktu połączenia z usługą, przejdź w wierszu polecenia do folderu zawierającego to narzędzie, a następnie uruchom polecenie:  **serviceconnectiontool.exe**.  

|Opcje wiersza polecenia|Szczegóły|  
|---------------------------|-------------|  
|**-prepare -usagedatadest [dysk:][ścieżka][nazwapliku.cab]**|To polecenie zapisuje bieżące dane użycia w pliku cab.<br /><br /> Polecenie to uruchom jako **administrator lokalny** na serwerze, który jest hostem punktu połączenia z usługą.<br /><br /> Przykład:   **-prepare -usagedatadest D:\USB\Usagedata.cab**|    
|**-connect -usagedatasrc [napęd:][ścieżka] -updatepackdest [napęd:][ścieżka] -proxyserveruri [nazwa_FQDN_serwera_proxy] -proxyusername [nazwa_użytkownika]** <br /> <br /> W przypadku używania wersji programu Configuration Manager wcześniejszej niż 1606 należy określić nazwę pliku cab i nie można używać opcji dla serwera proxy.  Obsługiwane parametry polecenia są następujące: <br /> **-connect -usagedatasrc [napęd:][ścieżka][nazwa_pliku] -updatepackdest [napęd:][ścieżka]** |To polecenie służy do nawiązywania połączenia z usługą Configuration Manager w chmurze w celu przekazywania plików cab danych użycia z określonej lokalizacji oraz do pobierania dostępnych pakietów aktualizacji i zawartości konsoli. Opcje dotyczące serwerów proxy są opcjonalne.<br /><br /> Polecenie to uruchom jako **administrator lokalny** na komputerze mającym połączenie z Internetem.<br /><br /> Przykład dotyczący nawiązywania połączenia bez użycia serwera proxy: **-connect -usagedatasrc D:\USB\ -updatepackdest D:\USB\UpdatePacks** <br /><br /> Przykład dotyczący nawiązywania połączenia z użyciem serwera proxy: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks -proxyserveruri itgproxy.redmond.corp.microsoft.com -proxyusername Meg** <br /><br /> W przypadku używania wersji wcześniejszej niż 1606 należy określić nazwę pliku cab, natomiast nie można określić serwera proxy. Użyj następującego przykładowego wiersza polecenia: **-connect -usagedatasrc D:\USB\Usagedata.cab -updatepackdest D:\USB\UpdatePacks**|      
|**-import -updatepacksrc [dysk:][ścieżka]**|To polecenie importuje pakiety aktualizacji i zawartość konsoli, którą wcześniej pobrano do konsoli programu Configuration Manager.<br /><br /> Polecenie to uruchom jako **administrator lokalny** na serwerze, który jest hostem punktu połączenia z usługą.<br /><br /> Przykład:  **-import -updatepacksrc D:\USB\UpdatePacks**|  
|**-export -dest [dysk:][ścieżka][nazwapliku.csv]**|To polecenie eksportuje dane użycia do pliku csv, którego zawartość można później obejrzeć.<br /><br /> Polecenie to uruchom jako **administrator lokalny** na serwerze, który jest hostem punktu połączenia z usługą.<br /><br /> Przykład: **-export -dest D:\USB\usagedata.csv**|  

