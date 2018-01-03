---
title: "Zarządzanie klientami"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zarządzać klientami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3986a992-c175-4b6f-922e-fc561e3d7cb7
caps.latest.revision: "17"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 2065fd0910b1d89df3f8296c87ede15b89331568
ms.sourcegitcommit: 528b1ce79803fecd34937a790e9b5cde282d4caa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manage-clients-in-system-center-configuration-manager"></a>Jak zarządzać klientami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Gdy klient programu Configuration Manager instaluje na urządzeniu i pomyślnie przypisze do lokacji, zobacz urządzenia w **zasoby i zgodność** obszaru roboczego w **urządzeń** węzła w jedną lub więcej kolekcje w programie **kolekcje urządzeń** węzła. Po wybraniu urządzenia lub kolekcji, mogą wykonywać operacje zarządzania. Istnieją inne sposoby zarządzania klientem, które mogą dotyczyć innych obszarów roboczych w konsoli lub zadań poza konsoli.  

> [!NOTE]  
>  Jeśli klient programu Configuration Manager jest zainstalowany, ale jeszcze nie pomyślnie przypisany do lokacji, może nie być wyświetlana w konsoli. Po Przypisywanie klienta do lokacji, zaktualizuj członkostwo w kolekcji, a następnie Odśwież widok konsoli.  
>   
>  Ponadto urządzenie może również wyświetlane w konsoli, gdy nie jest zainstalowany klient programu Configuration Manager. Dzieje się w stanie, jeśli urządzenie zostało wykryte, ale klient nie jest zainstalowany i przypisany. 
>
> Urządzenia przenośne zarządzane przy użyciu łącznika serwera Exchange i urządzeniami zarejestrowanymi w usłudze Microsoft Intune nie należy instalować klienta programu Configuration Manager.  
>   
>  Użyj **klienta** kolumny w konsoli programu Configuration Manager w celu ustalenia, czy klient jest zainstalowany, aby można było zarządzać nim z konsoli.  

##  <a name="BKMK_ManagingClients_DevicesNode"></a> Zarządzanie klientami z poziomu węzła Urządzenia  

W zależności od typu urządzenia, niektóre z tych opcji mogą być niedostępne.  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** >  **urządzeń**.  

3.  Wybierz co najmniej jedno urządzenie, a następnie wybierz jedną z tych zadań zarządzania klientami na Wstążce lub klikając prawym przyciskiem myszy urządzenie:  

    -   **Zarządzanie informacjami o koligacji urządzenia użytkownika**  

         Konfigurowanie skojarzenia między użytkownikami a urządzeniami, można efektywnie wdrażania oprogramowania dla użytkowników.  

         Zobacz [Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md)  

    -   **Dodanie urządzenia do nowej lub istniejącej kolekcji**  

         Urządzenia można dodać do kolekcji przy użyciu reguły bezpośredniej.  

    -   **Instalacja i ponowna instalacja klienta za pomocą kreatora wypychania klienta**  

         Instalację i ponowną instalację klienta programu Configuration Manager do naprawy lub ponownej konfiguracji. Ta opcja obejmuje ustawienia konfiguracji witryny i właściwości pliku client.msi, które można ustawić dla instalacji wypychanej klienta.  

        > [!TIP]  
        >  Istnieje wiele różnych sposobów instalacji (i ponownej instalacji) klienta programu Configuration Manager. Mimo że Kreator wypychania klienta stanowi wygodny sposób metody instalacji klienta, ponieważ można go uruchomić z konsoli, ta metoda ma wiele zależności i nie jest odpowiednia dla wszystkich środowisk. Aby uzyskać więcej informacji o zależnościach, zobacz [Wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md). Aby uzyskać więcej informacji o innych metodach instalowania klientów, zobacz [Metody instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/client-installation-methods.md).  

         Zobacz [Jak zainstalować klientów programu Configuration Manager za pomocą instalacji wypychanej klienta](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush).  

    -   **Ponowne przypisanie lokacji**  

         Można ponownie przypisać jednego lub kilku klientów do innej lokacji głównej w hierarchii, uwzględniając zarządzane urządzenia przenośne. Klientów można przypisywać ponownie pojedynczo lub wybierać wielu klientów i przypisywać ich zbiorczo do nowej lokacji.  

    -   **Zdalne administrowanie klientem**  

         Uruchom Eksploratora zasobów do wyświetlania informacji spisu sprzętu i oprogramowania z klienta systemu Windows. Zdalne administrowanie urządzenia przy użyciu zdalnego sterowania, pomocy zdalnej lub pulpitu zdalnego.  

         Zobacz [jak używać Eksploratora zasobów do wyświetlania spisu sprzętu](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) i [jak używać Eksploratora zasobów do wyświetlania spisu oprogramowania](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

         Zobacz [zdalne administrowanie komputerem klienckim z systemem Windows](../../../core/clients/manage/remote-control/remotely-administer-a-windows-client-computer.md).  

    -   **Zatwierdzenie klienta**  

         Gdy klient komunikuje się z systemami lokacji przy użyciu protokołu HTTP i certyfikatu z podpisem własnym, należy zatwierdzić tych klientów, aby zidentyfikować ich jako zaufane komputery. Domyślnie konfiguracja lokacji powoduje automatyczne zatwierdzenie klientów z tego samego lasu usługi Active Directory i zaufanych lasów, aby nie trzeba było ręcznie zatwierdzać każdego klienta. Jednak należy ręcznie zatwierdzić zaufane komputery grupy roboczej i innych niezatwierdzonych komputerów, którym ufasz.  

        > [!WARNING]  
        >  Mimo że niektóre funkcje zarządzania mogą działać w przypadku niezatwierdzonych klientów, jest to nieobsługiwany scenariusz dla programu Configuration Manager.  

         Jest konieczne zatwierdzanie klientów, którzy zawsze komunikują się z systemami lokacji przy użyciu protokołu HTTPS lub klientów, którzy używają certyfikatów PKI podczas komunikowania się z systemami lokacji przy użyciu protokołu HTTP. Ci klienci ustanawiają zaufania za pomocą certyfikatów PKI.  

    -   **Zablokowanie lub odblokowanie klienta**  

         Zablokowany klient, który nie jest już zaufany. Blokada uniemożliwia odebranie zasad klienta oraz uniemożliwia komunikację z klientem przez systemów lokacji.  

        > [!WARNING]  
        >  Tylko zablokowanie klienta zapobiega komunikacji z klienta z systemami lokacji programu Configuration Manager i nie zapobiega komunikacji z innymi urządzeniami. Ponadto, gdy klient komunikuje się z systemami lokacji za pomocą protokołu HTTP zamiast HTTPS, istnieją pewne ograniczenia dotyczące zabezpieczeń.  

         Można także odblokować klienta, który jest zablokowany. 

         Zobacz [Określanie, czy blokować klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

    -   **Usunięcie wymaganego wdrożenia PXE**  

         Należy ponownie wdrożyć wymagane wdrożenia PXE dla komputera.  

         Zobacz [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE w programie System Center Configuration Manager](../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   **Zarządzanie właściwościami klienta**  

         Wyświetl dane wykrywania i wdrożenia docelowe dla klienta. Można również skonfigurować zmienne używane przez sekwencje zadań do wdrożenia systemu operacyjnego na urządzeniu.  

    -   **Usunięcie klienta**  

        > [!WARNING]  
        >  Nie należy usuwać klienta, aby odinstalować klienta programu Configuration Manager lub usuń go z kolekcji.  

         **Usunąć** akcja umożliwia ręczne usunięcie rekordu klienta z bazy danych programu Configuration Manager i zwykle, nie należy używać tej akcji, z wyjątkiem w rozwiązywaniu problemów. Usunięcie rekordu klienta, ale klient jest nadal zainstalowany i komunikacji z lokacją, wykrywanie interwału czasowego ponownie utworzy rekord klienta. Rekord klienta zostanie wyświetlony ponownie w konsoli programu Configuration Manager, ale Historia klienta i poprzednie skojarzenia zostaną utracone.  

        > [!NOTE]  
        >  Po usunięciu klienta urządzenia przenośnego, które było rejestrowane przez program Configuration Manager, ta akcja powoduje także odwołanie certyfikatu PKI wydanego dla urządzenia przenośnego, a certyfikat następnie zostanie odrzucony przez punkt zarządzania nawet wtedy, gdy usługi IIS nie sprawdza listy CRL. Po usunięciu tych klientów certyfikaty na starszych klientach urządzeń przenośnych nie zostaną odwołane.  

         Aby odinstalować klienta, patrz [Dezinstalacja klienta programu Configuration Manager](#BKMK_UninstalClient).  

         Aby przypisać klienta do nowej lokacji głównej, zobacz [Jak przypisać klientów do lokacji w programie System Center Configuration Manager](../../../core/clients/deploy/assign-clients-to-a-site.md).  

         Aby usunąć klienta z kolekcji, należy ponownie skonfigurować właściwości kolekcji. Zobacz [Zarządzanie kolekcjami w programie System Center Configuration Manager](../../../core/clients/manage/collections/manage-collections.md).  

    -   **Wymazanie urządzenia przenośnego**  

         Można wymazać urządzenia przenośne, które obsługują polecenia wymazywania.  

         Ta akcja powoduje trwałe usunięcie wszystkich danych na urządzeniu przenośnym, w tym ustawienia osobiste i dane osobiste. Zwykle wykonanie tej akcji powoduje przywrócenie domyślnych ustawień fabrycznych urządzenia przenośnego. Czyszczenie urządzenia przenośnego, gdy urządzenie przenośne nie jest już zaufany. Na przykład w przypadku utraty lub kradzieży urządzenia.  

        > [!TIP]  
        >  Sprawdź w dokumentacji producenta Aby uzyskać więcej informacji na temat sposobu przetwarzania przez urządzenie przenośne polecenia wymazywania.  

         Występuje często opóźnienie, dopóki urządzenie przenośne odbierze polecenie wymazania:  

        -   Jeśli urządzenie przenośne zostało zarejestrowane przez program Configuration Manager lub Microsoft Intune, klient odbierze polecenie po pobraniu zasad klienta.  

        -   Jeśli urządzenie przenośne jest zarządzane przez łącznik serwera Exchange, odbierze polecenie podczas synchronizacji z programem Exchange.  

         Można użyć **stan wymazania** kolumny w celu monitorowania odebrania polecenia wymazania przez urządzenie. Dopóki urządzenie wysyła potwierdzenia wymazania do programu Configuration Manager, możesz anulować polecenie czyszczenia.  

    -   **Wycofanie urządzenia przenośnego**  

         **Wycofaj** opcja jest obsługiwana tylko przez urządzenia przenośne zarejestrowane przez program Microsoft Intune lub na\-lokalnych zarządzania urządzeniami przenośnymi.  

         Aby uzyskać więcej informacji, zobacz [Łatwiejsza ochrona danych dzięki funkcjom czyszczenia danych, zdalnego blokowania lub resetowania kodu dostępu przy użyciu programu System Center Configuration Manager](../../../mdm/deploy-use/wipe-lock-reset-devices.md).  

    -   **Zmiana własności urządzenia**  

         Jeśli urządzenie nie jest przyłączony do domeny i nie jest zainstalowany klient programu Configuration Manager, należy użyć tej opcji można zmienić własności do **firmy** lub **osobistych**.  

         Tej wartości można użyć w wymaganiach aplikacji w celu kontroli wdrożeń oraz do sterowania ilości zapasów zbieranych z urządzeń użytkowników.  

        Może być konieczne dodanie **właściciel urządzenia** kolumny do widoku, klikając prawym przyciskiem myszy nagłówek dowolnej kolumny, a następnie wybierając go.

         Aby uzyskać więcej informacji, zobacz [Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

##  <a name="BKMK_ManagingClients_DeviceCollectionsNode"></a>Zarządzanie klientami z węzła kolekcje urządzeń  
  Wiele zadań, które są dostępne dla urządzeń w **urządzeń** węzła są również dostępne w kolekcji. Konsolę automatycznie stosuje operacji do wszystkich kwalifikujących się urządzeń w kolekcji. Ta akcja na całą kolekcję generuje pakietów sieciowych dodatkowe i zwiększa użycie procesora CPU na serwerze lokacji.  

  Należy rozważyć przed wykonaniem zadań na poziomie kolekcji. Po rozpoczęciu nie można zatrzymać zadania z poziomu konsoli. 
 - Ile urządzeń jest kolekcja?
 - Urządzenia są połączone przez połączenia sieciowe o niskiej przepustowości?
 - Ile czasu jest to zadanie, trzeba wykonać dla wszystkich urządzeń?

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
Począwszy od wersji 1710, można użyć konsoli programu Configuration Manager do zidentyfikowania klientów, które wymagają ponownego uruchomienia komputera. Następnie użyj akcji powiadomienia klienta, aby uruchomić je ponownie.

> [!Tip]
> Klienci musi również uaktualnić do wersji 1710 dla tej funkcji do funkcji. Firma Microsoft zaleca, aby włączyć automatyczne uaktualnianie klienta aktualności klientów z koszty administracyjne do minimum. Aby uzyskać więcej informacji, zobacz [użycie automatycznego uaktualnienia klienta](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#use-automatic-client-upgrade).

Aby zidentyfikować urządzenia, które oczekują na ponowne uruchomienie komputera, przejdź do **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager i wybierz **urządzeń** węzła. Następnie wyświetlić stan dla każdego urządzenia w okienku szczegółów w nowej kolumnie o nazwie **oczekujące ponowne uruchomienie**. Każde urządzenie ma co najmniej jeden z następujących wartości: 
 - **Nie**: nie oczekiwania na ponowne uruchomienie nie istnieje
 - **Menedżer konfiguracji**: Ta wartość pochodzi z składnik koordynatora ponowne uruchomienie komputera klienta (RebootCoordinator.log)
 - **Zmiany nazwy pliku**: Ta wartość pochodzi z raportowania operacji zmiany nazwy plików oczekujących (Menedżer HKLM\SYSTEM\CurrentControlSet\Control\Session, PendingFileRenameOperations) systemu Windows
 - **Usługi Windows Update**: Ta wartość pochodzi z usługi Windows Update Agent raportowania oczekuje na ponowne uruchomienie jest wymagane dla co najmniej jednej aktualizacji (HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\WindowsUpdate\Auto Update\RebootRequired)
 - **Dodaj lub Usuń funkcję**: Ta wartość pochodzi z obsługi systemu Windows na podstawie składnika raportowania dodawania lub usuwania funkcji systemu Windows wymaga ponownego uruchomienia (HKLM\Software\Microsoft\Windows\CurrentVersion\Component na podstawie Servicing\Reboot Oczekujące)

**Aby utworzyć powiadomienie klienta, aby ponownie uruchomić urządzenie:**
1.  Znajdź urządzenia, które chcesz ponownie uruchomić w ramach kolekcji w **kolekcje urządzeń** węzła konsoli.
2.  Kliknij prawym przyciskiem myszy na urządzeniu, wybierz opcję **powiadomienie klienta**, a następnie wybierz **ponownego uruchomienia**. Otwiera okno informacje o ponownym uruchomieniu. Kliknij przycisk **OK** o potwierdzenie żądania ponownego uruchomienia.

Po otrzymaniu powiadomienia przez klienta, **Centrum oprogramowania** zostanie otwarte okno powiadomienia informują użytkownika o ponowne uruchomienie. Domyślnie uruchomiony ponownie po upływie 90 minut. Można zmodyfikować czas ponownego uruchamiania, konfigurując [ustawień klienta](/sccm/core/clients/deploy/configure-client-settings). Ustawienia zachowania ponownego uruchamiania znajdują się na [ponownego uruchomienia komputera](/sccm/core/clients/deploy/about-client-settings#computer-restart) karta Ustawienia domyślne.


##  <a name="BKMK_ClientCache"></a> Konfiguracja pamięci podręcznej klienta w klientach programu Configuration Manager  
Pamięci podręcznej klienta są przechowywane pliki tymczasowe dla instalowania klientów, aplikacje i programy. Aktualizacje oprogramowania również używać pamięci podręcznej klienta, ale zawsze próbuje pobrać bez względu na ustawienie rozmiaru pamięci podręcznej. Skonfiguruj ustawienia pamięci podręcznej, takich jak rozmiar i położenie, podczas ręcznej instalacji klienta, w przypadku używania instalacji wypychanej klienta lub po instalacji.

Począwszy od programu Configuration Manager 1606 wersji, można określić rozmiar folderu pamięci podręcznej przy użyciu ustawień klienta w konsoli programu Configuration Manager.   

 Lokalizacja domyślna pamięci podręcznej klienta programu Configuration Manager to %*windir*%\ccmcache a domyślna ilość miejsca to 5120 MB.  

> [!IMPORTANT]  
>  Nie należy szyfrować folderu, w którym znajduje się pamięć podręczna klienta. Program Configuration Manager nie może pobierać zawartości do folderu szyfrowanego.  

### <a name="about-client-cache"></a>Informacje o pamięci podręcznej klienta  

Klient programu Configuration Manager pobiera zawartość do wymaganego oprogramowania zaraz po otrzymaniu wdrożenia, ale uruchamia go do momenty określonej godziny wdrożenia. Klienta programu Configuration Manager w zaplanowanym terminie, sprawdza, czy zawartość jest dostępna w pamięci podręcznej. Jeśli zawartość znajduje się w pamięci podręcznej jest niepoprawna, klient korzysta z zawartości w pamięci podręcznej. Po zmianie wymagana wersja zawartości lub klienta spowoduje usunięcie zawartości, aby zwolnić miejsce dla inny pakiet, klient pobiera zawartość do pamięci podręcznej ponownie.  

Jeśli klient próbuje pobrać zawartość dla programu lub aplikacji, która jest większa niż rozmiar pamięci podręcznej, wdrożenie zakończy się niepowodzeniem ze względu na rozmiar za mało pamięci podręcznej. Klient generuje komunikat o stanie 10050 dla rozmiaru za mało pamięci podręcznej. Jeśli później możesz zwiększyć rozmiar pamięci podręcznej, wynik jest:  

-   Dla wymaganego programu: Klient nie rozpocznie automatycznego ponownego pobierania zawartości. Należy ponownie wdrożyć pakiet i program do klienta.  
-   Dla wymaganej aplikacji: Klient automatycznie ponowi próbę pobrania zawartości po pobraniu zasad klienta.  

Jeśli klient spróbuje pobrać pakiet, który jest mniejszy od rozmiaru pamięci podręcznej, ale pamięć podręczna jest pełna, wszystkie wymagane wdrożenia ponawiać do momentu miejsca w pamięci podręcznej jest dostępna, limitu czasu pobierania lub liczbę ponownych prób osiągnie limit. Po późniejszym zwiększeniu rozmiaru pamięci podręcznej klienta programu Configuration Manager próbuje pobrać pakiet ponownie podczas kolejnego interwału ponownej próby. Klient próbuje pobrać zawartość co 4 godziny i maksymalnie 18 razy.  

Zawartość z pamięci podręcznej nie jest automatycznie usuwana, lecz pozostaje w pamięci podręcznej przynajmniej przez jeden dzień po jej użyciu. Konfigurowanie właściwości pakietu z opcją trwałości zawartości w pamięci podręcznej oznacza, że klient nie usunie automatycznie zawartości pakietu z pamięci podręcznej. Jeśli miejsca w pamięci podręcznej jest używany przez pakiety pobrane w ciągu ostatnich 24 godzin, a klient musi pobrać nowe pakiety, możesz zwiększyć rozmiar pamięci podręcznej, lub wybierz opcję, aby usunąć utrwaloną zawartość pamięci podręcznej.  

 Aby skonfigurować pamięć podręczną klienta przy ręcznej instalacji klienta lub po jego zainstalowaniu, wykonaj następującą procedurę.  

### <a name="to-configure-the-client-cache-when-you-install-clients-by-using-manual-client-installation"></a>Aby skonfigurować pamięć podręczną klienta przy ręcznej instalacji klientów  

Uruchom polecenie CCMSetup.exe z lokalizacji źródłowej i podaj wartości potrzebnych z poniższych właściwości, rozdzielając je spacjami:  

   -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Dla wersji 1606, użyj ustawienia rozmiaru pamięci podręcznej dostępne w **ustawień klienta** w konsoli programu Configuration Manager, zamiast SMSCACHESIZE. Aby uzyskać więcej informacji, zobacz [ustawienia pamięci podręcznej klienta](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

Aby uzyskać więcej informacji na temat używania tych właściwości wiersza polecenia programu CCMSetup.exe, zobacz [o właściwościach instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-when-you-install-clients-by-using-client-push-installation"></a>Aby skonfigurować pamięć podręczną klienta przy wypychanej instalacji klientów  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny**.  

3.  Wybierz odpowiednią witrynę i na **Home** karcie **ustawienia** grupy, wybierz **ustawienia instalacji klienta** > **właściwości instalacji**.  

5.  Określ następujące właściwości, rozdzielając je spacjami:  

    -   DISABLECACHEOPT  

    -   SMSCACHEDIR  

    -   SMSCACHEFLAGS  

    -   SMSCACHESIZE  

        > [!NOTE]
        > Dla wersji 1606, użyj ustawienia rozmiaru pamięci podręcznej dostępne w **ustawień klienta** w konsoli programu Configuration Manager, zamiast SMSCACHESIZE. Aby uzyskać więcej informacji, zobacz [ustawienia pamięci podręcznej klienta](../../../core/clients/deploy/about-client-settings.md#client-cache-settings).

       Aby uzyskać więcej informacji na temat używania tych właściwości wiersza polecenia programu CCMSetup.exe, zobacz [o właściwościach instalacji klienta](../../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="to-configure-the-client-cache-folder-on-the-client-computer"></a>Aby skonfigurować folder pamięci podręcznej klienta na komputerze klienckim  

1.  Na komputerze klienckim, przejdź do **programu Configuration Manager** w Panelu sterowania i kliknij dwukrotnie, aby wyświetlić właściwości.  

2.  Na **pamięci podręcznej** kartę Ustaw właściwości miejsca i lokalizacji. Lokalizacja domyślna to *%windir%*\ccmcache.  

3.  Aby usunąć pliki w folderze pamięci podręcznej, wybierz pozycję **Usuń pliki**.  

### <a name="to-configure-client-cache-size-in-client-settings"></a>Aby skonfigurować rozmiar pamięci podręcznej klienta w ustawieniach klienta

Dostosuj rozmiar pamięci podręcznej klienta bez konieczności ponownej instalacji klienta, konfigurując rozmiar pamięci podręcznej w konsoli programu Configuration Manager przy użyciu ustawień klienta.  

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
 Configuration Manager używa identyfikatora sprzętu próbuje identyfikować klientów, którzy mogą stanowić duplikaty, alertów rekordy powodujące konflikt. Na przykład w przypadku ponownej instalacji komputera, identyfikator sprzętu będzie taki sam, ale identyfikator GUID używany przez program Configuration Manager może ulec zmianie.  

 Menedżer konfiguracji automatycznie rozwiązuje konflikty przy użyciu uwierzytelniania systemu Windows dla konta komputera lub certyfikat PKI z zaufanego źródła. Jednak jeśli programu Configuration Manager nie może rozwiązać konflikt identyfikatorów zduplikowane sprzętu, ustawienia hierarchii, określa, czy mają być automatycznie scalić rekordy lub pozwala określić zachowanie. Jeśli zdecydujesz o ręcznym zarządzaniu zduplikowanymi rekordami należy ręcznie rozwiązać rekordy powodujące konflikt w konsoli programu Configuration Manager.  


#### <a name="to-change-the-hierarchy-setting-for-managing-conflicting-records"></a>Aby zmienić hierarchię ustawień przy zarządzaniu rekordami powodującymi konflikt  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny** > **ustawienia hierarchii**
2.  Na **zatwierdzania klienta i rekordy powodujące konflikt** , wybierz pozycję albo **automatycznie rozwiązuj rekordy powodujące konflikt**, lub **ręcznie rozwiązuj rekordy powodujące konflikt**.  

#### <a name="to-manually-resolve-conflicting-records"></a>Aby ręcznie rozwiązać rekordy powodujące konflikt  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie** > **stan systemu** > **rekordy powodujące konflikt**.  

3.  Wybierz co najmniej jeden rekordy powodujące konflikt, a następnie wybierz pozycję **rekord powodujący konflikt**.  

4.  Wybierz jedną z następujących opcji:  

    -   **Scal** połączyć nowo wykryte rekordy z istniejącym rekordem klienta.  

    -   **Nowy** , aby utworzyć nowy rekord dla rekordu powodującego konflikt.  

    -   **Zablokuj** , aby utworzyć nowy rekord dla rekordu powodującego konflikt, ale oznaczyć go jako zablokowany.  

## <a name="manage-duplicate-hardware-identifiers"></a>Zarządzanie sprzętu zduplikowane identyfikatory
Udostępnia listę sprzętu rozruch identyfikatorów, które Menedżera konfiguracji ignoruje na potrzeby środowiska PXE i rejestracji klienta pomaga dwóch typowych problemów.

1. Wiele nowych urządzeń, takich jak 3 Surface Pro, nie dołączaj wewnętrznego portu sieci Ethernet. Pracownicy techniczni Użyj karty USB do Ethernet do nawiązywania połączenia przewodowego dla celów wdrożenia systemu operacyjnego. Jednak te karty często są współużytkowane z powodu kosztów i użyteczność ogólne. Ponieważ adresu MAC ta karta służy do identyfikowania urządzenia, ponowne użycie karty staje się problemem bez administratora dodatkowe akcje między każdym wdrożeniu. Aby ponownie użyć karty w tym scenariuszu, należy wykluczyć jej adres MAC.
2. Gdy atrybut SMBIOS powinna być unikatowa, niektóre urządzenia specjalistyczne ma zduplikowane identyfikatory. Wyklucz ten zduplikowany identyfikator i polegać na unikatowy adres MAC każdego urządzenia.

#### <a name="to-add-hardware-identifiers-for-configuration-manager-to-ignore"></a>Aby dodać identyfikatory sprzętu dla programu Configuration Manager do ignorowania  
1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**.
2. Na **Home** karcie **witryny** grupy, wybierz **ustawienia hierarchii**.
3. Na **zatwierdzania klienta i rekordy powodujące konflikt** , wybierz pozycję **Dodaj** w **zduplikowane identyfikatory sprzętu** sekcji, aby dodać nowe identyfikatory sprzętu.

##  <a name="BKMK_PolicyRetrieval"></a> Inicjowanie pobierania zasad dla klienta programu Configuration Manager  
 Klient programu Configuration Manager systemu Windows pobiera zasady klienta zgodnie z harmonogramem skonfigurowanym jako ustawienie klienta. Jednak może być niektórych sytuacjach potrzebne do rozpoczęcia pobierania na żądanie od klienta, na przykład do rozwiązywania problemów lub testowania.  

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

2.  Na **akcje** , wybierz pozycję **cykl maszyny zasady pobierania i szacowania** zainicjować zasady komputera, a następnie wybierz pozycję **Uruchom teraz**.  

4.  Wybierz **OK** aby potwierdzić monit.  

5.  Powtórz kroki 3 i 4 dla wszystkich potrzebnych działań, takich jak **Cykl pobierania i szacowania zasad użytkownika** w ustawieniach klienta u użytkownika.  

#### <a name="manually-initiate-client-policy-retrieval-by-script"></a>Ręcznie rozpocząć pobieranie zasad klienta za pomocą skryptu  

1.  Otwórz edytor tekstu, na przykład Notatnik.  

2.  Skopiuj i Wstaw następujący przykładowy kod Visual Basic Scripting Edition do pliku:  

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
