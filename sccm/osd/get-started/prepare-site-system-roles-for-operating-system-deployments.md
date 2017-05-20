---
title: "Przygotowanie ról systemu lokacji dla wdrożeń systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Przed przystąpieniem do wdrażania systemów operacyjnych w programie System Center Configuration Manager, należy skonfigurować role systemu lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0ef5f3ce-b0e4-4775-b5c2-b245e45b4194
caps.latest.revision: 11
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: 11c0f169afebdb071fefb5ce300fd1ae3481a94f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-site-system-roles-for-operating-system-deployments-with-system-center-configuration-manager"></a>Przygotowanie ról systemu lokacji do wdrożeń systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Do wdrażania systemów operacyjnych w programie System Center Configuration Manager, należy najpierw przygotować następującą witrynę role systemu, które wymagają określonej konfiguracji i uwagi.

##  <a name="BKMK_DistributionPoints"></a> Punkty dystrybucji  
 Rola systemu lokacji punktu dystrybucji zawiera pliki źródłowe do pobrania przez klientów, takie jak zawartość aplikacji, aktualizacje oprogramowania, obrazy systemu operacyjnego i obrazy rozruchowe. Dystrybucję zawartości można kontrolować, korzystając opcji dotyczących przepustowości, ograniczania przepustowości i planowania.  

 Koniecznie upewnij się, że masz wystarczająco dużo punktów dystrybucji, aby obsłużyć wdrożenie systemów operacyjnych na komputerach. Koniecznie zaplanuj również rozmieszczenie tych punktów dystrybucji w hierarchii. Można znaleźć większość tych informacji w planowaniu [zarządzania infrastrukturą zawartości i](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md). Należy jednak wziąć pod uwagę pewne dodatkowe kwestie związane z punktami dystrybucji, specyficzne dla wdrożenia systemu operacyjnego.  

###  <a name="BKMK_AdditionalPlanning"></a> Dodatkowe kwestie związane z planowaniem punktów dystrybucji  
 Należy wziąć pod uwagę następujące dodatkowe kwestie związane z planowaniem punktów dystrybucji:  

-   **Jak mogę zapobiec niepożądanym wdrożeniom systemu operacyjnego?**  

     Menedżer konfiguracji nie rozróżnia serwerów lokacji od komputerów docelowych w kolekcji. Jeśli wymagana sekwencja zadań jest wdrażana w kolekcji zawierającej serwer lokacji, serwer ten wykonuje sekwencję zadań tak samo jak każdy inny komputer w kolekcji. Należy upewnić się, że wdrożenie systemu operacyjnego korzysta z kolekcji zawierającej klientów, którzy mają uruchamiać wdrożenie.  

     Można zarządzać zachowaniem wdrożeń sekwencji zadań wysokiego ryzyka. Wdrożenie wysokiego ryzyka to wdrożenie, które jest instalowane automatycznie na kliencie i może mieć niepożądane skutki. Przykładem może być sekwencja zadań, której cel to „Wymagane” i która wdraża system operacyjny. Aby zmniejszyć ryzyko niepożądanych wdrożeń o wysokim ryzyku, można skonfigurować ustawienia weryfikacji wdrażania: Aby uzyskać więcej informacji, zobacz [ustawienia do zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   **Na ilu komputerach można jednocześnie wdrożyć obraz systemu operacyjnego z pojedynczego punktu dystrybucji?**  

     Aby oszacować liczbę potrzebnych punktów dystrybucji, należy wziąć pod uwagę szybkość przetwarzania oraz wydajność we/wy dysku punktu dystrybucji, dostępną przepustowość sieci oraz wpływ, jaki rozmiar pakietu obrazu ma na te zasoby. Na przykład w sieci Ethernet o szybkości 100 megabajtów (MB) maksymalna liczba komputerów, jaka umożliwia przetworzenie pakietów obrazu rozmiaru 4 gigabajtów (GB) w jedną godzinę, to 11, jeśli nie są brane pod uwagę żadne inne zasoby serwera.  

     `100 Megabits/sec = 12.5 Megabytes/sec = 750 Megabytes/min = 45 Gigabytes/hour = 11 images @ 4GB per image.`  

     Jeśli jest konieczne wdrożenie systemu operacyjnego na konkretnej liczbie komputerów w określonym przedziale czasu, należy dokonać dystrybucji obrazu do odpowiedniej liczby punktów dystrybucji.  

-   **Czy mogę wdrożyć system operacyjny w punkcie dystrybucji?**  

     Można wdrożyć system operacyjny w punkcie dystrybucji, ale obraz systemu operacyjnego musi być pobrany z innego punktu dystrybucji.  

###  <a name="BKMK_PXEDistributionPoint"></a> Konfigurowanie punktów dystrybucji do akceptowania żądań PXE  
 Do wdrażania systemów operacyjnych klientów programu Configuration Manager, uniemożliwiających żądania rozruchu środowiska PXE, należy skonfigurować co najmniej jeden punkt dystrybucji do akceptowania żądań PXE. Po skonfigurowaniu punktu dystrybucji będzie on odpowiadać na żądania rozruchu PXE oraz podejmować decyzje dotyczące wykonywania akcji wdrażania.

> [!IMPORTANT]  
>  [Usługi wdrażania systemu Windows](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_WDS) muszą być zainstalowane we wszystkich punktach dystrybucji obsługujących żądania PXE.  

 Aby zmodyfikować istniejący punkt dystrybucji tak, aby akceptował żądania PXE, należy wykonać poniższą procedurę. Aby uzyskać więcej informacji na temat sposobu instalowania nowego punktu dystrybucji, zobacz [Instalowanie lub modyfikowanie punktu dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).  

#### <a name="to-modify-an-existing-distribution-point-to-accept-pxe-requests"></a>Aby zmodyfikować istniejący punkt dystrybucji tak, aby akceptował żądania PXE  

1.  W konsoli programu Configuration Manager kliknij **Administracja**, rozwiń węzeł **Przegląd** i kliknij przycisk **punktów dystrybucji**.  

2.  Wybierz punkt dystrybucji, który chcesz skonfigurować, i na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

3.  Na stronie właściwości punktu dystrybucji kliknij kartę **PXE** . Wybierz pozycję **Włącz obsługę środowiska PXE dla klientów** , aby włączyć obsługę środowiska PXE w tym punkcie dystrybucji.  

4.  Kliknij pozycję **Tak** w oknie dialogowym **Sprawdzenie wymaganych portów dla środowiska PXE** , aby potwierdzić, że chcesz włączyć obsługę środowiska PXE. Menedżer konfiguracji automatycznie konfiguruje domyślnych portów w Zaporze systemu Windows. Jeśli jednak używasz innej zapory, musisz ręcznie skonfigurować porty.  

    > [!NOTE]  
    >  Jeśli usługi WDS i DHCP są zainstalowane na tym samym serwerze, należy skonfigurować usługi WDS do nasłuchiwania na innym porcie (ponieważ usługa DHCP nasłuchuje na tym samym porcie). Aby uzyskać więcej informacji, zobacz [Zagadnienia dotyczące sytuacji, gdy na tym samym serwerze istnieją Usługi wdrażania systemu Windows i protokół DHCP](../plan-design/infrastructure-requirements-for-operating-system-deployment.md#BKMK_WDSandDHCP).  

5.  Aby włączyć usługi wdrażania systemu Windows, tak aby odpowiadały na żądania obsługi PXE, zaznacz pole wyboru **Zezwól temu punktowi dystrybucji na odpowiadanie na przychodzące żądania środowiska PXE** . Możesz użyć tego ustawienia, aby włączać i wyłączać usługę bez usuwania funkcji PXE z punktu dystrybucji.  

6.  Wybierz **Włącz obsługę nieznanych komputerów** do wdrażania systemów operacyjnych na komputerach, które nie są zarządzane przez program Configuration Manager.  

7.  Wybierz pozycję **Wymagaj hasła, kiedy komputery używają środowiska PXE**i podaj silne hasło, aby zapewnić dodatkową ochronę wdrożeń PXE.  

8.  Na liście **Koligacja urządzenia użytkownika** wybierz, w jaki sposób punkt dystrybucji ma kojarzyć użytkowników z komputerem docelowym w ramach wdrożeń PXE.  

    -   Wybierz pozycję **Nie używaj koligacji urządzenia użytkownika** , aby nie kojarzyć użytkowników z komputerem docelowym.  

    -   Wybierz pozycję **Zezwalaj na koligację urządzenia użytkownika z zatwierdzaniem ręcznym** , aby czekać na zatwierdzenie przez użytkownika administracyjnego przed skojarzeniem użytkowników z komputerem docelowym.  

    -   Wybierz pozycję **Zezwalaj na koligację urządzenia użytkownika z automatycznym zatwierdzeniem** , aby automatycznie kojarzyć użytkowników z komputerem docelowym bez czekania na zatwierdzenie.  

     Aby uzyskać więcej informacji, zobacz [kojarzyć użytkowników z komputerem docelowym](../get-started/associate-users-with-a-destination-computer.md).  

9. Określ, czy punkt dystrybucji ma odpowiadać na żądania PXE ze wszystkich interfejsów sieciowych, czy tylko z konkretnych interfejsów sieciowych. Jeśli punkt dystrybucji ma odpowiadać na konkretnych interfejsach sieciowych, podaj adres MAC każdego interfejsu sieciowego.  

10. Określ w sekundach opóźnienie oczekiwania punktu dystrybucji przed udzieleniem odpowiedzi na żądanie komputera, gdy jest używanych wiele punktów dystrybucji z włączoną funkcją PXE.  

11. Kliknij przycisk **OK** , aby zaktualizować właściwości punktu dystrybucji.  

###  <a name="BKMK_RamDiskTFTP"></a> Dostosowywanie rozmiaru okna i bloku RamDisk TFTP w punktach dystrybucji z obsługą środowiska PXE  
Można dostosować rozmiar bloku RamDisk TFTP, a począwszy od programu Configuration Manager w wersji 1606, rozmiar okna dla punktów dystrybucji z włączoną obsługą środowiska PXE. Jeśli skonfigurowano sieć, może to powodować niepowodzenie pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu, ponieważ rozmiar bloku lub okna jest zbyt duży. Dostosowanie rozmiaru bloku i rozmiaru okna RamDisk TFTP umożliwia zoptymalizowanie ruchu TFTP w środowisku PXE w celu spełnienia określonych wymagań sieciowych.   
Aby określić najbardziej wydajne rozwiązanie, należy przetestować dostosowane ustawienia w swoim środowisku.  

-   **Rozmiar bloku TFTP**: Rozmiar bloku jest rozmiar pakietów danych, które są wysyłane przez serwer do klienta, który pobiera plik (zgodnie z opisem w dokumencie RFC 2347). Większy rozmiar bloku zezwala serwerowi na wysyłanie mniejszej liczby pakietów, co przekłada się na zmniejszenie obustronnych opóźnień między serwerem a klientem. Niemniej jednak duże rozmiary bloków powodują fragmentowanie pakietów. Większość wdrożeń klienckich środowiska PXE nie obsługuje pakietów po fragmentacji.  

-   **Rozmiar okna TFTP**: TFTP wymaga pakietu potwierdzenie (ACK) dla każdego bloku danych, które są wysyłane. Serwer nie wyśle kolejnego bloku, dopóki nie odbierze pakietu ACK dla poprzedniego bloku. Dostosowywanie okien TFTP jest funkcją Usług wdrażania systemu Windows, która umożliwia określenie liczby bloków danych potrzebnych do wypełnienia okna. Serwer wysyła bloki danych symetrycznie, dopóki okno nie zostanie wypełnione, a następnie klient wysyła pakiet ACK. Zwiększenie rozmiaru okna redukuje liczbę obustronnych opóźnień między klientem a serwerem i zmniejsza całkowity czas wymagany do pobrania obrazu rozruchowego.  


#### <a name="to-modify-the-ramdisk-tftp-window-size"></a>Aby zmienić rozmiar okna RamDisk TFTP  

-   Dodaj następujący klucz rejestru w punktach dystrybucji obsługujących środowisko PXE, aby skonfigurować rozmiar okna RamDisk TFTP:  

     **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Nazwa: RamDiskTFTPWindowSize  

     **Typ**: REG_DWORD  

     **Wartość**: &lt;dostosować rozmiar okna >  

 Wartość domyślna to 1 (1 blok danych będzie wypełniać okno).  

#### <a name="to-modify-the-ramdisk-tftp-block-size"></a>Aby zmienić rozmiar bloku RamDisk TFTP  

-   Dodaj następujący klucz rejestru w punktach dystrybucji obsługujących środowisko PXE, aby skonfigurować rozmiar okna RamDisk TFTP:  

     **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
    Nazwa: RamDiskTFTPBlockSize  

     **Typ**: REG_DWORD  

     **Wartość**: &lt;dostosować rozmiar bloku >  

 Wartość domyślna to 4096 (4k).  


###  <a name="BKMK_DPMulticast"></a> Konfigurowanie punktów dystrybucji pod kątem obsługi multiemisji  
 Multiemisja to metoda optymalizacji sieci, której można użyć dla punktów dystrybucji, gdy wielu klientów może jednocześnie pobierać ten sam obraz systemu operacyjnego. W przypadku multiemisji obraz systemu operacyjnego jest udostępniony w punkcie dystrybucji i może być jednocześnie pobierany na wiele komputerów. Punkt dystrybucji nie musi wysyłać kopii danych do każdego klienta w ramach oddzielnego połączenia. Obsługa multiemisji wymaga skonfigurowania co najmniej jednego punktu dystrybucji. Aby uzyskać więcej informacji, zobacz [użyć multiemisji w celu wdrożenia systemu operacyjnego Windows za pośrednictwem sieci](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 Przed wdrożeniem systemu operacyjnego należy skonfigurować punkt dystrybucji do obsługi multiemisji. Aby zmodyfikować istniejący punkt dystrybucji do obsługi multiemisji, należy wykonać poniższą procedurę. Aby uzyskać informacje o sposobie instalowania nowego punktu dystrybucji, zobacz [instalowania i konfigurowania punktów dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md).

#### <a name="to-enable-multicast-for-a-distribution-point"></a>Aby włączyć multiemisję dla punktu dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Przegląd**, a następnie wybierz węzeł **Punkty dystrybucji** .  

3.  Wybierz punkt dystrybucji, który ma być używany do multiemisji obrazu systemu operacyjnego.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

5.  Wybierz kartę **Multiemisja** i skonfiguruj poniższe opcje:  

    -   **Włącz multiemisję**: Należy wybrać tę opcję, aby punkt dystrybucji do obsługi multiemisji.  

    -   **Konto połączenia multiemisji**: Określ konto w celu połączenia z bazą danych lokacji.  

    -   **Ustawienia adresu multiemisji**: Określ adresy IP do przesyłania danych do komputerów docelowych. Domyślnie adres IP jest pobierany z serwera DHCP, na którym jest włączona funkcja dystrybucji adresów multiemisji. W zależności od środowiska sieciowego możesz określić zakres adresów IP między 239.0.0.0 i 239.255.255.255.  

        > [!IMPORTANT]  
        >  Te adresy IP muszą być dostępne dla komputerów docelowych, które żądają obrazu systemu operacyjnego. Oznacza to, że routery i zapory między komputerem docelowym a serwerem lokacji muszą być skonfigurowane tak, aby zezwalały na ruch multiemisji.  

    -   **Zakres portów UDP**: Określ zakres portów UDP w celu wysyłania danych do komputerów docelowych.  

        > [!IMPORTANT]  
        >  Te porty muszą być dostępne dla komputerów docelowych, które żądają obrazu systemu operacyjnego. Oznacza to, że routery i zapory między komputerem docelowym a serwerem lokacji muszą być skonfigurowane tak, aby zezwalały na ruch multiemisji.  

    -   **Włącz zaplanowaną multiemisję**: Określ, jak program Configuration Manager sterować uruchamianiem wdrażania systemów operacyjnych na komputerach docelowych. Kliknij opcję **Włącz zaplanowaną multiemisję**, a następnie wybierz jedną z poniższych opcji.  

         W **opóźnienie rozpoczęcia sesji** Określ liczbę minut, które program Configuration Manager czeka przed udzieleniem odpowiedzi na pierwsze żądanie wdrożenia.  

         W **minimalna wielkość sesji** Określ, ile żądań musi odebrać przed uruchomieniem programu Configuration Manager do wdrażania systemu operacyjnego.  

    -   **Szybkość przesyłu**: Wybierz szybkość przesyłu w celu pobierania danych na komputerach docelowych.  

    -   **Maksymalna liczba klientów**: Określ maksymalną liczbę komputerów docelowych, które mogą pobierać system operacyjny z tego punktu dystrybucji.  

6.  Kliknij przycisk **OK**.  

##  <a name="BKMK_StateMigrationPoints"></a> Punkt migracji stanu  
 Punkt migracji stanu przechowuje dane stanu użytkownika przechwycone na jednym komputerze, a następnie przywrócone na innym komputerze. Jednak w przypadku przechwytywania ustawień użytkownika na potrzeby wdrożenia systemu operacyjnego na tym samym komputerze, na przykład w ramach wdrożenia polegającego na odświeżeniu systemu operacyjnego komputera docelowego, możesz wybrać, czy dane mają być przechowywane na tym samym komputerze przy użyciu twardych linków, czy za pomocą punktu migracji stanu. Dla niektórych wdrożeń komputerów podczas tworzenia Magazyn stanów, program Configuration Manager automatycznie tworzy skojarzenie między magazynem stanów i komputerem docelowym. Planując punkt migracji stanu, należy uwzględnić wymienione niżej kwestie.  

### <a name="user-state-size"></a>Rozmiar danych stanu użytkownika  
 Rozmiar danych stanu użytkownika bezpośrednio wpływa na magazyn dyskowy punktu migracji stanu oraz na wydajność sieci w czasie migracji. Należy uwzględnić rozmiar danych stanu użytkownika oraz liczbę komputerów, do których odbywa się migracja. Należy także wziąć pod uwagę, jakie ustawienia są migrowane z komputera. Jeśli na przykład folder **Moje dokumenty** ma już kopię zapasową na serwerze, być może jego migracja w ramach wdrożenia obrazu nie jest konieczna. Unikanie niepotrzebnych migracji może zmniejszyć ogólny rozmiar danych stanu użytkownika oraz ograniczyć jego wpływ na wydajność sieci oraz magazyn dyskowy punktu migracji stanu.  

### <a name="user-state-migration-tool"></a>Narzędzie do migracji stanu użytkowników  
 Aby przechwycić i przywrócić stan użytkownika podczas wdrażania systemu operacyjnego, należy korzystać z pakietu Narzędzie do migracji stanu użytkowników (USMT), który wskazuje pliki źródłowe narzędzia USMT. Menedżer konfiguracji automatycznie tworzy ten pakiet w konsoli programu Configuration Manager w **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **pakiety**. Program Configuration Manager używa 10.0 narzędzia USMT, które jest dystrybuowane w Windows Assessment and Deployment Kit (Windows ADK), aby przechwycić stan użytkownika z jednego systemu operacyjnego, a następnie przywróć ją do innego systemu operacyjnego.  

 Aby uzyskać opis różnych scenariuszy migracji dla narzędzia USMT 10.0, zobacz [Common Migration Scenarios](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)(Typowe scenariusze migracji).  

### <a name="retention-policy"></a>Zasady przechowywania  
 Podczas konfigurowania punktu migracji stanu można określić, jak długo punkt przechowuje dane stanu użytkownika. Czas przechowywania danych na punkcie migracji stanu zależy od dwóch kwestii:  

-   Wpływ przechowywanych danych na magazyn dyskowy  

-   Potencjalny wymóg przechowywania danych przez pewien czas na wypadek ponownej migracji danych  

 Migracja stanu odbywa się w dwóch fazach: Przechwytywanie danych i przywracanie danych. Podczas przechwytywania dane stanu użytkownika są zbierane i zapisywane w punkcie migracji stanu. Podczas przywracania dane stanu użytkownika są pobierane z punktu migracji stanu i zapisywane na komputerze docelowym. Następnie zapisane dane są zwalniane w kroku **Zwolnij magazyn stanów** sekwencji zadań. Po uwolnieniu danych następuje włączenie licznika czasu przechowywania. W przypadku wybrania opcji natychmiastowego usunięcia zmigrowanych danych dane stanu użytkownika zostaną usunięte natychmiast po uwolnieniu. W przypadku wybrania opcji zachowania danych przez pewien czas dane zostaną usunięte po upływie tego czasu, liczonego od chwili uwolnienia danych. Im dłuższy czas przechowywania, tym więcej związanej z tym wymaganej przestrzeni dyskowej.  

### <a name="select-drive-to-store-user-state-migration-data"></a>Wybieranie dysku do zapisania danych migracji stanu użytkownika  
 Podczas konfigurowania punktu migracji stanu należy określić dysk serwera, na którym mają być przechowywane migrowane dane stanu użytkownika. Dysk można wybrać z listy. Niektóre dyski widoczne na liście mogą jednak być dyskami niezapisywalnymi, takimi jak napęd CD lub dysk niebędący udziałem sieciowym. Dodatkowo niektóre litery dysków mogą nie być mapowane do żadnych dysków na komputerze. Podczas konfigurowania punktu migracji stanu należy wskazać zapisywalny, udostępniony dysk.  

### <a name="configure-a-state-migration-point"></a>Konfigurowanie punktu migracji stanu  
 Poniższe metody pozwalają skonfigurować punkt migracji stanu, tak aby przechowywać w nich dane o stanie użytkownika.  

-   Użyj **Kreatora tworzenia serwera systemu lokacji** , aby utworzyć nowy serwer systemu lokacji dla punktu migracji stanu.  

-   Użyj **Kreatora dodawania ról systemu lokacji** , aby dodać punkt migracji stanu do istniejącego serwera.  

 Korzystając z tych kreatorów, należy podać następujące informacje dotyczące punktu migracji stanu:  

-   Foldery do przechowywania danych o stanie użytkownika.  

-   Maksymalna liczba klientów, którzy mogą przechowywać dane w punkcie migracji stanu.  

-   Minimalna ilość wolnego miejsca dla punktu migracji stanu, w którym będą przechowywane dane o stanie użytkownika.  

-   Zasady usuwania dla nowej roli. Istnieje możliwość określenia, aby dane o stanie użytkownika były usuwane natychmiast, po ich przywróceniu na komputerze, albo po upływie określonej liczby dni od ich przywrócenia.  

-   Czy punkt migracji stanu odpowiada tylko na żądania przywrócenia danych stanu użytkownika. Włączenie tej opcji uniemożliwia użycie punktu migracji stanu do przechowywania danych o stanie użytkownika.  

 Kroki, aby zainstalować rolę systemu lokacji, można znaleźć w temacie [Dodaj role systemu lokacji](../../core/servers/deploy/configure/add-site-system-roles.md).  

