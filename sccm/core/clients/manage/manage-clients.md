---
title: "Zarządzanie klientami"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zarządzać klientami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: "17"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: ae1bc53cf15b2a1746656667f7bf546742432c11
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Jak zarządzać klientami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po zainstalowaniu klienta programu System Center Configuration Manager i przypisane do lokacji programu Configuration Manager, urządzenie będzie widoczne **zasoby i zgodność** obszaru roboczego w **urządzeń** węzła w co najmniej jednej kolekcji w **kolekcje urządzeń** węzła. Po wybraniu urządzenia lub kolekcji, mogą wykonywać operacje zarządzania. Istnieją także inne sposoby zarządzania klientem, które mogą dotyczyć innych obszarów roboczych w konsoli lub zadań, które nie używają konsoli programu Configuration Manager.  

> [!NOTE]  
>  Klient programu Configuration Manager może być zainstalowany, ale nie są wyświetlane w konsoli programu Configuration Manager. Może to nastąpić, jeśli klient jeszcze nie pomyślnie przypisany do lokacji, konsola musi zostać odświeżona lub członkostwo w kolekcji zaktualizowane.  
>   
>  Ponadto urządzenie może również wyświetlane w konsoli, gdy nie jest zainstalowany klient programu Configuration Manager. Może to nastąpić, jeśli urządzenie zostało wykryte, ale klient programu Configuration Manager nie jest zainstalowany i przypisany. Urządzenia przenośne, które są zarządzane przy użyciu łącznika serwera Exchange i urządzeń, które są zarejestrowane w usłudze Microsoft Intune, nie instaluj klienta programu Configuration Manager.  
>   
>  Użyj **klienta** kolumny w konsoli programu Configuration Manager w celu ustalenia, czy klient programu Configuration Manager jest zainstalowany, aby można było zarządzać nim z konsoli programu Configuration Manager.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Zarządzanie klientami z poziomu węzła Urządzenia  

Należy zauważyć, że w zależności od typu urządzenia, niektóre z tych opcji mogą być niedostępne.  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** >  **urządzeń**.  

3.  Wybierz co najmniej jedno urządzenie, a następnie wybierz jedną z tych zadań zarządzania klientami na Wstążce lub klikając prawym przyciskiem myszy urządzenie:  

    -   **Zarządzanie informacjami o koligacji urządzenia użytkownika**  

         Konfigurowanie skojarzenia między użytkownikami a urządzeniami, można efektywnie wdrażania oprogramowania dla użytkowników.  

         Zobacz [Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)  

    -   **Dodanie urządzenia do nowej lub istniejącej kolekcji**  

         Urządzenia można dodać do kolekcji przy użyciu reguły bezpośredniej.  

    -   **Instalacja i ponowna instalacja klienta za pomocą kreatora wypychania klienta**  

         Instalację i ponowną instalację klienta programu Configuration Manager w celu jego naprawy lub ponownej konfiguracji na komputerach z systemem Windows. Zawiera opcje konfiguracji lokacji i właściwości pliku client.msi, które można ustawić dla instalacji wypychanej klienta.  

        > [!TIP]  
        >  Istnieje wiele różnych sposobów instalacji (i ponownej instalacji) klienta programu Configuration Manager. Mimo że Kreator wypychania klienta stanowi wygodny sposób metody instalacji klienta, ponieważ można go uruchomić z konsoli, ta metoda ma wiele zależności i nie jest odpowiednia dla wszystkich środowisk. Aby uzyskać więcej informacji o zależnościach, zobacz [Wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md). Aby uzyskać więcej informacji o innych metodach instalowania klientów, zobacz [Metody instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md).  

         Zobacz [Jak zainstalować klientów programu Configuration Manager za pomocą instalacji wypychanej klienta](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Ponowne przypisanie lokacji**  

         Można ponownie przypisać jednego lub kilku klientów do innej lokacji głównej w hierarchii, uwzględniając zarządzane urządzenia przenośne. Klientów można przypisywać ponownie pojedynczo lub wybierać wielu klientów i przypisywać ich zbiorczo do nowej lokacji.  

    -   **Zdalne administrowanie klientem**  

         Można uruchomić Eksplorator zasobów, aby zobaczyć informacje o spisie sprzętu i oprogramowania z klienta z systemem Windows i zarządzać nim zdalnie, używając funkcji Zdalne sterowanie, Pomoc zdalna lub Pulpit zdalny.  

         Zobacz [Jak używać Eksploratora zasobów do wyświetlania spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) i [Jak używać Eksploratora zasobów do wyświetlania spisu oprogramowania w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Zobacz [Zdalne administrowanie komputerem klienckim z systemem Windows za pomocą programu System Center Configuration Manager](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Zatwierdzenie klienta**  

         Gdy klient komunikuje się z systemami lokacji przy użyciu protokołu HTTP i certyfikatu z podpisem własnym, należy zatwierdzić tych klientów, aby zidentyfikować ich jako zaufane komputery. Domyślnie konfiguracja lokacji powoduje automatyczne zatwierdzenie klientów z tego samego lasu usługi Active Directory i zaufanych lasów, aby nie trzeba było ręcznie zatwierdzać każdego klienta. Należy jednak ręcznie zatwierdzić zaufane komputery grupy roboczej i inne zaufane, ale niezatwierdzone komputery.  

        > [!WARNING]  
        >  Mimo że niektóre funkcje zarządzania mogą działać w przypadku niezatwierdzonych klientów, jest to nieobsługiwany scenariusz dla programu Configuration Manager.  

         Jest konieczne zatwierdzanie klientów, którzy zawsze komunikują się z systemami lokacji przy użyciu protokołu HTTPS lub klientów, którzy używają certyfikatów PKI podczas komunikowania się z systemami lokacji przy użyciu protokołu HTTP. Ci klienci ustanawiają zaufania za pomocą certyfikatów PKI.  

    -   **Zablokowanie lub odblokowanie klienta**  

         Klienta, który nie jest już zaufany, aby uniemożliwić mu odebranie zasad klienta i zapobiec systemy lokacji programu Configuration Manager komunikację z jej zablokować.  

        > [!WARNING]  
        >  Tylko zablokowanie klienta zapobiega komunikacji z klienta z systemami lokacji programu Configuration Manager i nie zapobiega komunikacji z innymi urządzeniami. Ponadto, gdy klient komunikuje się z systemami lokacji za pomocą protokołu HTTP zamiast HTTPS, istnieją pewne ograniczenia dotyczące zabezpieczeń.  

         Można odblokować zablokowanego klienta. Jednakże, jeżeli zostanie odblokowany komputer Intel AMT udostępniony dla funkcji AMT, gdy był zablokowany, aby ponownie zarządzać tym komputerem poza pasmem, należy wykonać dodatkowe czynności.  

         Zobacz [Określanie, czy blokować klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Usunięcie wymaganego wdrożenia PXE**  

         Należy ponownie wdrożyć wymagane wdrożenia PXE dla komputera.  

         Zobacz [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE w programie System Center Configuration Manager](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **Zarządzanie właściwościami klienta**  

         Wyświetl dane wykrywania i wdrożenia docelowe dla klienta. Można również skonfigurować zmienne używane przez sekwencje zadań do wdrożenia systemu operacyjnego na urządzeniu.  

    -   **Usunięcie klienta**  

        > [!WARNING]  
        >  Nie należy usuwać klienta, aby odinstalować klienta programu Configuration Manager lub usuń go z kolekcji.  

         **Usunąć** akcja umożliwia ręczne usunięcie rekordu klienta z bazy danych programu Configuration Manager i zwykle, nie należy używać tej akcji, z wyjątkiem w rozwiązywaniu problemów. Jeśli rekord klienta zostanie usunięty, a klient jest nadal zainstalowany i komunikacji z programem Configuration Manager, wykrywanie interwału czasowego ponownie utworzy rekord klienta i pojawi się on w konsoli programu Configuration Manager, ale Historia klienta i poprzednie skojarzenia zostaną utracone.  

        > [!NOTE]  
        >  Po usunięciu klienta urządzenia przenośnego, które było rejestrowane przez program Configuration Manager, ta akcja powoduje także odwołanie certyfikatu PKI wydanego dla urządzenia przenośnego, a certyfikat następnie zostanie odrzucony przez punkt zarządzania nawet wtedy, gdy usługi IIS nie sprawdza listy CRL. Po usunięciu tych klientów certyfikaty na starszych klientach urządzeń przenośnych nie zostaną odwołane.  

         Aby odinstalować klienta, patrz [Dezinstalacja klienta programu Configuration Manager](#BKMK_UninstalClient).  

         Aby przypisać klienta do nowej lokacji głównej, zobacz [Jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

         Aby usunąć klienta z kolekcji, należy ponownie skonfigurować właściwości kolekcji. Zobacz [Zarządzanie kolekcjami w programie System Center Configuration Manager](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Wymazanie urządzenia przenośnego**  

         Można wymazać urządzenia przenośne, które obsługują polecenia wymazywania.  

         Ta akcja powoduje trwałe usunięcie wszystkich danych na urządzeniu przenośnym, w tym ustawienia osobiste i dane osobiste. Zwykle wykonanie tej akcji powoduje przywrócenie domyślnych ustawień fabrycznych urządzenia przenośnego. Czyszczenie urządzeń przenośnych, gdy urządzenie przenośne nie jest już zaufany, przykład w przypadku utraty lub kradzieży.  

        > [!TIP]  
        >  Sprawdź w dokumentacji producenta Aby uzyskać więcej informacji na temat sposobu przetwarzania przez urządzenie przenośne polecenia wymazywania.  

         Występuje często opóźnienie, dopóki urządzenie przenośne odbierze polecenie wymazania:  

        -   Jeśli urządzenie przenośne zostało zarejestrowane przez program Configuration Manager lub Microsoft Intune, klient odbierze polecenie po pobraniu zasad klienta.  

        -   Jeśli urządzenie przenośne jest zarządzane przez łącznik serwera Exchange, odbierze polecenie podczas synchronizacji z programem Exchange.  

         Można użyć **stan wymazania** kolumny w celu monitorowania odebrania polecenia wymazania przez urządzenie. Polecenie wymazania można anulować do momentu wysłania przez urządzenie potwierdzenia wymazania do programu Configuration Manager.  

    -   **Wycofanie urządzenia przenośnego**  

         **Wycofaj** opcja jest obsługiwana tylko przez urządzenia przenośne, które są zarejestrowane przez usługę Intune lub usługę na\-lokalnych zarządzanie urządzeniami przenośnymi.  

         Aby uzyskać więcej informacji, zobacz [Łatwiejsza ochrona danych dzięki funkcjom czyszczenia danych, zdalnego blokowania lub resetowania kodu dostępu przy użyciu programu System Center Configuration Manager](../../../mdm/deploy-use/wipe-lock-reset-devices.md).  

    -   **Zmiana własności urządzenia**  

         Własność urządzeń można zmienić **firmy** lub **osobistych** Jeśli urządzenie nie jest przyłączony do domeny i nie jest zainstalowany klient programu Configuration Manager.  

         Tej wartości można użyć w wymaganiach aplikacji w celu kontroli wdrożeń oraz do sterowania ilości zapasów zbieranych z urządzeń użytkowników.  

        Może być konieczne dodanie **właściciel urządzenia** kolumny do widoku, klikając prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie wybierając go.

         Aby uzyskać więcej informacji, zobacz [Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a> Zarządzanie klientami z poziomu węzła Kolekcje urządzeń  
  Wiele zadań, które można wykonać na jednym urządzeniu lub na wielu urządzeniach w **urządzeń** węzeł może odbywać się w kolekcji. Operacja zostanie automatycznie stosuje do wszystkich kwalifikujących się urządzeń w kolekcji. Należy pamiętać, że generuje dużą liczbę pakietów sieciowych i zwiększa użycie procesora CPU na serwerze lokacji.  

  Przed wykonaniem zadań zarządzania na poziomie kolekcji należy uwzględnić liczbę zadań w kolekcji, określić, czy korzystają z połączeń sieciowych o niskiej przepustowości oraz czas wykonania zadania dla wszystkich urządzeń. Po rozpoczęciu nie można zatrzymać zadania z poziomu konsoli.  

#### <a name="to-manage-clients-from-the-device-collections-node"></a>Aby zarządzać klientami z węzła Kolekcje urządzeń  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcje urządzeń**.  

3.  Wybierz kolekcję, a następnie wybierz jedną z następujących zadań zarządzania klientami na Wstążce lub klikając prawym przyciskiem myszy kolekcję. Te zadania zarządzania klientami można *tylko* można wykonać na poziomie kolekcji.  

    -   **Skanowanie komputerów pod kątem złośliwego oprogramowania i pobranie plików definicji oprogramowania chroniącego przed złośliwym kodem**  

         Zobacz [programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

    -   **Wdrożenie oprogramowania, linii bazowych konfiguracji i sekwencji zadań.**  

         Zobacz:  

        -   [Wdrażanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/deploy-use/deploy-software-updates.md)  

        -   [Planowanie i konfigurowanie ustawień zgodności w programie System Center Configuration Manager](../../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

    -   **Konfigurowanie ustawień zarządzania energią**  

         Zobacz [Tworzenie i stosowanie planów zasilania w programie System Center Configuration Manager](../../../core/clients/manage/power/create-and-apply-power-plans.md). Planów zasilania można użyć tylko w przypadku komputerów z systemem Windows.  

    -   **Powiadomienie komputerów o jak najszybszym pobraniu zasad**  

         Powiadomić wybranych klientów systemu Windows w celu pobierania zasad komputera, jak najszybciej poza interwał sondowania zasad klienta za pomocą powiadomień klienta.  

         Zadania powiadamiania klientów są wyświetlane w węźle **Operacje klienta** w obszarze roboczym **Monitorowanie** .  


## <a name="restart-clients"></a>Uruchom ponownie klientów
Począwszy od wersji 1710, można użyć konsoli programu Configuration Manager do identyfikowania urządzenia klienckie, które wymagają ponownego uruchomienia a następnie użyć akcji powiadamiania klienta uruchomić je ponownie.

Aby zidentyfikować urządzenia, które oczekują na ponowne uruchomienie komputera, przejdź do **zasoby i zgodność** > **urządzeń** i wybrać odpowiednią kolekcję z urządzeniami, które mogą wymagać ponownego uruchomienia komputera. Po wybraniu kolekcji można wyświetlić stan dla każdego urządzenia w okienku szczegółów w nowej kolumnie o nazwie **oczekujące ponowne uruchomienie**. Każde urządzenie ma wartość **tak**, lub **nr**.

**Aby utworzyć powiadomienie klienta, aby ponownie uruchomić urządzenie:**
1.  Znajdź urządzenie, którego chcesz ponownie uruchomić komputer w węźle urządzenia w konsoli.
2.  Kliknij prawym przyciskiem myszy na urządzeniu, wybierz opcję **powiadomienie klienta**, a następnie wybierz **ponownego uruchomienia**. Spowoduje to otwarcie okna informacje o ponownym uruchomieniu. Kliknij przycisk **OK** o potwierdzenie żądania ponownego uruchomienia.

Po otrzymaniu powiadomienia przez klienta, **Centrum oprogramowania** zostanie otwarte okno powiadomienia informują użytkownika o ponowne uruchomienie. Domyślnie uruchomiony ponownie po upływie 90 minut. Można zmodyfikować czas ponownego uruchamiania, konfigurując [ustawień klienta](/sccm/core/clients/deploy/configure-client-settings). Ustawienia zachowania ponownego uruchamiania znajdują się na [ponownego uruchomienia komputera](/sccm/core/clients/deploy/about-client-settings#computer-restart) karta Ustawienia domyślne.




##  <a name="BKMK_ClientCache"></a> Konfiguracja pamięci podręcznej klienta w klientach programu Configuration Manager  
Pamięci podręcznej klienta są przechowywane pliki tymczasowe dla instalowania klientów, aplikacje i programy. Choć aktualizacje oprogramowania również używają pamięci podręcznej klienta, to nie są ograniczone jej rozmiarem i zawsze będą do niej pobierane. Można skonfigurować ustawienia pamięci podręcznej klienta, takich jak rozmiar i położenie, po zainstalowaniu klienta programu Configuration Manager ręcznie, korzystając z instalacji wypychanej klienta lub po zainstalowaniu klienta.

Począwszy od programu Configuration Manager 1606 wersji, można określić rozmiar folderu pamięci podręcznej przy użyciu ustawień klienta w konsoli programu Configuration Manager.   

 Lokalizacja domyślna pamięci podręcznej klienta programu Configuration Manager to %*windir*%\ccmcache a domyślna ilość miejsca to 5120 MB.  

> [!IMPORTANT]  
>  Nie należy szyfrować folderu, w którym znajduje się pamięć podręczna klienta. Program Configuration Manager nie może pobierać zawartości do folderu szyfrowanego.  

### <a name="about-client-cache"></a>Informacje o pamięci podręcznej klienta  

Klient programu Configuration Manager pobiera zawartość do wymaganego oprogramowania zaraz po otrzymaniu wdrożenia, ale uruchamia go do momenty określonej godziny wdrożenia. Klienta programu Configuration Manager w zaplanowanym terminie, sprawdza, czy zawartość jest dostępna w pamięci podręcznej. Jeśli zawartość znajduje się w pamięci podręcznej jest niepoprawna, klient korzysta z zawartości w pamięci podręcznej. Gdy wymagana wersja zawartości została zmieniona lub zawartość została usunięta w celu przygotowania miejsca na inny pakiet, zawartość zostanie ponownie pobrana do pamięci podręcznej.  

Jeśli klient próbuje pobrać zawartość dla programu lub aplikacji, która jest większa niż rozmiar pamięci podręcznej, wdrożenie zakończy się niepowodzeniem ze względu na rozmiar za mało pamięci podręcznej i program Configuration Manager generuje identyfikator komunikatu o stanie 10050. Po późniejszym zwiększeniu rozmiaru pamięci podręcznej, wynik jest:  

-   Dla wymaganego programu: Klient nie rozpocznie automatycznego ponownego pobierania zawartości. Należy ponownie wdrożyć pakiet i program do klienta.  
-   Dla wymaganej aplikacji: Klient automatycznie ponowi próbę pobrania zawartości po pobraniu zasad klienta.  

Jeśli klient spróbuje pobrać pakiet, który jest mniejszy od rozmiaru pamięci podręcznej, ale pamięć podręczna jest pełna, wszystkie wymagane wdrożenia ponawiać dopóki miejsca w pamięci podręcznej jest dostępne, dopóki nie upłynie limit czasu pobierania lub aż do osiągnięcia limitu ponownych prób niepowodzenia miejsca w pamięci podręcznej. Po późniejszym zwiększeniu rozmiaru pamięci podręcznej klienta programu Configuration Manager próbuje pobrać pakiet ponownie podczas kolejnego interwału ponownej próby. Klient próbuje pobrać zawartość co 4 godziny i maksymalnie 18 razy.  

Zawartość z pamięci podręcznej nie jest automatycznie usuwana, lecz pozostaje w pamięci podręcznej przynajmniej przez jeden dzień po jej użyciu. Konfigurowanie właściwości pakietu z opcją trwałości zawartości w pamięci podręcznej oznacza, że klient nie usunie automatycznie zawartości pakietu z pamięci podręcznej. Jeśli przestrzeń na pamięć podręczną klienta jest zajęta przez pakiety pobrane w ciągu ostatnich 24 godzin, a klient musi pobrać nowe pakiety, możesz zwiększyć rozmiar pamięci podręcznej klienta lub usunąć zapisaną w pamięci podręcznej zawartość.  

 Aby skonfigurować pamięć podręczną klienta przy ręcznej instalacji klienta lub po jego zainstalowaniu, wykonaj następującą procedurę.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>Aby skonfigurować pamięć podręczną klienta przy ręcznej instalacji klientów  

Uruchom polecenie CCMSetup.exe z lokalizacji źródłowej i podaj wartości potrzebnych z poniższych właściwości, rozdzielając je spacjami:  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Dla wersji 1606, użyj ustawienia rozmiaru pamięci podręcznej dostępne w **ustawień klienta** w konsoli programu Configuration Manager, zamiast SMSCACHESIZE. Aby uzyskać więcej informacji, zobacz [Ustawienia pamięci podręcznej klienta](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

Aby uzyskać więcej informacji o sposobie używania tych właściwości wiersza polecenia programu CCMSetup.exe, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>Aby skonfigurować pamięć podręczną klienta przy wypychanej instalacji klientów  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz odpowiednią witrynę i na **Home** karcie **ustawienia** grupy, wybierz **ustawienia instalacji klienta** > **właściwości instalacji**.  

5.  Określ następujące właściwości, rozdzielając je spacjami:  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Dla wersji 1606, użyj ustawienia rozmiaru pamięci podręcznej dostępne w **ustawień klienta** w konsoli programu Configuration Manager, zamiast SMSCACHESIZE. Aby uzyskać więcej informacji, zobacz [Ustawienia pamięci podręcznej klienta](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

       Aby uzyskać więcej informacji o sposobie używania tych właściwości wiersza polecenia programu CCMSetup.exe, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>Aby skonfigurować folder pamięci podręcznej klienta na komputerze klienckim  

1.  Na komputerze klienckim, przejdź do **programu Configuration Manager** w Panelu sterowania i kliknij dwukrotnie, aby wyświetlić właściwości.  

2.  Na **pamięci podręcznej** kartę Ustaw właściwości miejsca i lokalizacji. Lokalizacja domyślna to *%windir%*\ccmcache.  

5.  Aby usunąć pliki w folderze pamięci podręcznej, wybierz pozycję **Usuń pliki**.  

    > [!NOTE]
    >
    > Folder pamięci podręcznej jest regularne folderze systemu Windows, co umożliwia automatyzację usunięcie zawartości folderu za pomocą skryptu, narzędzia, lub za pomocą polecenia cmdlet programu PowerShell `Remove-Item`.


### <a name="to-configure-client-cache-size-in-client-settings"></a>Aby skonfigurować rozmiar pamięci podręcznej klienta w ustawieniach klienta

Począwszy od wersji 1606, można dostosować rozmiar folderu pamięci podręcznej klienta bez konieczności ponownej instalacji klienta. W tym celu należy skonfigurować rozmiar pamięci podręcznej klienta w konsoli programu Configuration Manager w obszarze Ustawienia klienta.  

1. W konsoli programu Configuration Manager przejdź do obszaru **Administracja** > **Ustawienia klienta**.

2. Kliknij dwukrotnie przycisk **Ustawienia domyślne klienta**.
  Można również utworzyć niestandardowe ustawienia klienta, aby zastosować rozmiar pamięci podręcznej bardziej selektywnie. Aby uzyskać więcej informacji na temat domyślnych i niestandardowych ustawień klienta, zobacz [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).

 3. Wybierz **ustawienia pamięci podręcznej klienta** i wybierz polecenie **tak** dla **skonfiguruj rozmiar pamięci podręcznej klienta**, następnie użyć **MB** lub **odsetek ustawień dysku**. Rozmiar pamięci podręcznej jest dostosowywany do mniejszego z tych rozmiarów.

     Klient programu Configuration Manager skonfiguruje rozmiar pamięci podręcznej za pomocą tych ustawień podczas następnego pobierania zasad klienta.



##  <a name="BKMK_UninstalClient"></a> Dezinstalacja klienta programu Configuration Manager  
 Można odinstalować oprogramowanie klienckie programu Configuration Manager systemu Windows z komputera przy użyciu **CCMSetup.exe** z **/Uninstall** właściwości. Uruchom program CCMSetup.exe z komputera z wiersza polecenia lub wdróż pakiet i program dezinstalacji klienta z kolekcji komputerów.  

> [!WARNING]  
>  Nie można odinstalować klienta programu Configuration Manager z urządzenia przenośnego. Jeśli musisz usunąć klienta programu Configuration Manager z urządzeń przenośnych, należy wyczyścić urządzenia, co spowoduje usunięcie wszystkich danych na urządzeniu przenośnym.  

#### <a name="to-uninstall-the-configuration-manager-client-from-the-command-prompt"></a>Aby odinstalować klienta programu Configuration Manager z wiersza polecenia  

1.  Otwórz wiersz polecenia systemu Windows i wejdź do folderu, w którym znajduje się plik CCMSetup.exe.  

2.  Wpisz polecenie **Ccmsetup.exe /uninstall**i naciśnij klawisz **Enter**.  

> [!NOTE]  
>  Proces dezinstalacji wyświetla nie zwróciło żadnych wyników na ekranie. Aby sprawdzić, czy Dezinstalacja klienta zakończyła się pomyślnie, zapoznaj się z plikiem dziennika **CCMSetup.log** w folderze *%windir%\ ccmsetup* na komputerze klienckim.  

##  <a name="BKMK_ConflictingRecords"></a> Zarządzanie rekordami powodującymi konflikt w klientach programu Configuration Manager  
 Configuration Manager używa Identyfikatora sprzętu próbuje identyfikować klientów, którzy mogą stanowić duplikaty, alertów rekordy powodujące konflikt. Na przykład jeśli ponownej instalacji komputera jego identyfikator sprzętu będzie taki sam, ale identyfikator GUID używany przez program Configuration Manager może ulec zmianie.  

 W przypadku programu Configuration Manager może rozwiązać konflikt, stosując uwierzytelnianie systemu Windows dla konta komputera lub certyfikat PKI z zaufanego źródła, konflikt zostaje automatycznie rozwiązany. Jednak gdy programu Configuration Manager nie może rozwiązać konfliktu, używa ustawienia, które albo automatycznie scala rekordy, kiedy wykryje zduplikowane identyfikatory sprzętu (ustawienie domyślne), albo pozwala zadecydować o czasie scalania, blokowania lub tworzenia nowych rekordów klientów hierarchii. Jeśli zdecydujesz o ręcznym zarządzaniu zduplikowanymi rekordami należy ręcznie rozwiązać rekordy powodujące konflikt w konsoli programu Configuration Manager.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>Aby zmienić hierarchię ustawień przy zarządzaniu rekordami powodującymi konflikt  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny** > **ustawienia hierarchii**
2.  Na **zatwierdzania klienta i rekordy powodujące konflikt** , wybierz pozycję albo **automatycznie rozwiązuj rekordy powodujące konflikt**, lub **ręcznie rozwiązuj rekordy powodujące konflikt**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Aby ręcznie rozwiązać rekordy powodujące konflikt  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie** > **stan systemu** > **rekordy powodujące konflikt**.  

3.  Wybierz co najmniej jeden rekordy powodujące konflikt, a następnie wybierz pozycję **rekord powodujący konflikt**.  

4.  Wybierz jedną z poniższych opcji:  

    -   **Scal** połączyć nowo wykryte rekordy z istniejącym rekordem klienta.  

    -   **Nowy** , aby utworzyć nowy rekord dla rekordu powodującego konflikt.  

    -   **Zablokuj** , aby utworzyć nowy rekord dla rekordu powodującego konflikt, ale oznaczyć go jako zablokowany.  

## <a name="manage-duplicate-hardware-identifiers"></a>Zarządzanie sprzętu zduplikowane identyfikatory
Począwszy od 1610 wersji programu Configuration Manager, musisz podać listę identyfikatorów, które zignoruje programu Configuration Manager na potrzeby rejestracji rozruchu i klient PXE sprzętu. Istnieją dwie typowe problemy, które ułatwia to adres.

1. Wiele nowych urządzeń, takich jak 3 Surface Pro, nie dołączaj wewnętrznego portu sieci Ethernet. Karta USB do Ethernet jest zazwyczaj używany do ustanawiania połączenia przewodowego dla celów wdrożenia systemu operacyjnego. Jednak te są często udostępnionych kart z powodu kosztów i użyteczność ogólne. Ponieważ adresu MAC ta karta służy do identyfikowania urządzenia, ponowne użycie karty staje się problemem bez administratora dodatkowe akcje między każdym wdrożeniu. Z wersji 1610 dzięki czemu mogą być ponownie używane w tym scenariuszu można wykluczyć adres MAC tej karty.
2. Gdy identyfikator SMBIOS powinien być unikatowy identyfikator sprzętu, niektóre urządzenia specjalistyczne są tworzone za zduplikowane identyfikatory. Gdy nie jako wspólne jak w scenariuszu karty USB do Ethernet powyżej, listę identyfikatorów sprzętu może służyć do rozwiązania tego problemu, a także.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Aby dodać identyfikatory sprzętu dla programu Configuration Manager do ignorowania  
1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**.
2. Na **Home** karcie **witryny** grupy, wybierz **ustawienia hierarchii**.
3. Na **zatwierdzania klienta i rekordy powodujące konflikt** , wybierz pozycję **Dodaj** w **zduplikowane identyfikatory sprzętu** sekcji, aby dodać nowe identyfikatory sprzętu.

##  <a name="BKMK_PolicyRetrieval"></a> Inicjowanie pobierania zasad dla klienta programu Configuration Manager  
 Klient programu Configuration Manager systemu Windows pobiera zasady klienta zgodnie z harmonogramem skonfigurowanym jako ustawienie klienta. Jednak może być niektórych sytuacjach potrzebne, aby rozpocząć pobieranie zasad ad hoc z klienta, na przykład do rozwiązywania problemów lub testowania.  

Możesz zainicjować pobieranie zasad przy użyciu opcji:


- [Powiadomienie klienta](#initiate-client-policy-retrieval-using-client-notification)
- [**Akcje** kartę na kliencie](#manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client)
- [Skrypt](#manually-initiate-client-policy-retrieval-by-script)

> [!NOTE]  
>   
>  Informacje o ustawieniach pobierania zasad w klientach z systemem Linux i UNIX znajdują się w sekcji [Zasady komputera dla serwerów z systemami Linux i UNIX](../../../core/clients/manage/manage-clients-for-linux-and-unix-servers.md#BKMK_PolicyforLnU).  

#### <a name="initiate-client-policy-retrieval-using-client-notification"></a>Rozpocząć pobieranie zasad klienta za pomocą powiadomień klienta  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **kolekcje urządzeń**.  

3.  Zaznacz kolekcję urządzeń zawierającą komputery, na których chcesz pobrać zasady. Na **Home** karcie **kolekcje** grupy, wybierz **powiadomienie klienta** > **Pobierz zasady komputera**.  

    > [!NOTE]  
    >  Istnieje także możliwość użycia powiadomień klienta do rozpoczęcia pobierania dla przynajmniej jednego wybranego urządzenia wyświetlanego w węźle kolekcji tymczasowej, w węźle **Urządzenia** .  

#### <a name="manually-initiate-client-policy-retrieval-on-the-actions-tab-of-the-configuration-manager-client"></a>Ręcznie rozpocząć pobieranie zasad klienta na karcie Akcje klienta programu Configuration Manager  

1.  Wybierz polecenie **Configuration Manager** w Panelu sterowania komputera.  

2.  Na **akcje** wybierz kartę **cykl maszyny zasady pobierania i szacowania** zainicjować zasady komputera, a następnie wybierz pozycję **Uruchom teraz**.  

4.  Wybierz **OK** aby potwierdzić monit.  

5.  Powtórz kroki 3 i 4 dla wszystkich potrzebnych działań, takich jak **Cykl pobierania i szacowania zasad użytkownika** w ustawieniach klienta u użytkownika.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Ręcznie rozpocząć pobieranie zasad klienta za pomocą skryptu  

1.  Otwórz edytor tekstu, na przykład Notatnik.  

2.  Skopiuj i wstaw do pliku następujący tekst:  

    ```  
    on error resume next  

    dim oCPAppletMgr 'Control Applet manager object.  
    dim oClientAction 'Individual client action.  
    dim oClientActions 'A collection of client actions.  

    'Get the Control Panel manager object.  
    set  oCPAppletMgr=CreateObject("CPApplet.CPAppletMgr")  
    if err.number <> 0 then  
        Wscript.echo "Couldn't create control panel application manager"  
        WScript.Quit  
    end if  

    'Get a collection of actions.  
    set oClientActions=oCPAppletMgr.GetClientActions  
    if err.number<>0 then  
        wscript.echo "Couldn't get the client actions"  
        set oCPAppletMgr=nothing  
        WScript.Quit  
    end if  

    'Display each client action name and perform it.  
    For Each oClientAction In oClientActions  

        if oClientAction.Name = "Request & Evaluate Machine Policy" then  
            wscript.echo "Performing action " + oClientAction.Name   
            oClientAction.PerformAction  
        end if  
    next  

    set oClientActions=nothing  
    set oCPAppletMgr=nothing  
    ```  

3.  Zapisz plik z rozszerzeniem vbs.  

4.  Uruchom na kliencie zapisany plik na jeden z następujących sposobów:  

    -   Przejdź do pliku ze skryptem w Eksploratorze Windows i kliknij go dwukrotnie.  

    -   Otwórz wiersz polecenia i wpisz: **cscript &lt;ścieżka\nazwa_pliku.vbs >**.  

5.  Wybierz **OK** w **Host skryptów systemu Windows** okno dialogowe.  
