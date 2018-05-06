---
title: Przygotowanie ról systemu lokacji dla wdrożenia systemu operacyjnego
titleSuffix: Configuration Manager
description: Konfigurowanie ról systemu lokacji, przed przystąpieniem do wdrażania systemów operacyjnych
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 0ef5f3ce-b0e4-4775-b5c2-b245e45b4194
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c30c843c1b454b45483a2719eecf37334c8897e5
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prepare-site-system-roles-for-operating-system-deployments-with-system-center-configuration-manager"></a>Przygotowanie ról systemu lokacji do wdrożeń systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do wdrażania systemów operacyjnych w programie Configuration Manager, należy najpierw przygotować następujące witryny ról systemowych, które wymagają określonych konfiguracji i podjęcia.



##  <a name="BKMK_DistributionPoints"></a> Punkty dystrybucji  
 Rola systemu lokacji punktu dystrybucji zawiera pliki źródłowe do pobrania przez klientów. Ta zawartość jest dla aplikacji, aktualizacje oprogramowania, obrazy systemu operacyjnego, obrazy rozruchowe i pakiety sterowników. Dystrybucję zawartości można kontrolować, korzystając opcji dotyczących przepustowości, ograniczania przepustowości i planowania.  

 Jest ważne, że masz wystarczająco dużo punktów dystrybucji, aby obsłużyć wdrożenie systemów operacyjnych na komputerach. Należy również zaplanować rozmieszczenie tych punktów dystrybucji w hierarchii. Aby uzyskać więcej informacji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md). Ten artykuł zawiera niektóre dodatkowe zagadnienia związane z planowaniem punktów dystrybucji określonego do wdrażania systemu operacyjnego.  


###  <a name="BKMK_AdditionalPlanning"></a> Dodatkowe kwestie związane z planowaniem punktów dystrybucji  
 Dodatkowe planowanie rzeczy, które należy wziąć pod uwagę w przypadku punktów dystrybucji są następujące elementy:  

-   **Jak mogę zapobiec niepożądanych wdrożeń systemu operacyjnego**  

     Menedżer konfiguracji nie rozróżnia serwerów lokacji od innych komputerów docelowych w kolekcji. Wdrożenie sekwencji zadań wymaganych do kolekcji zawierającej serwer lokacji, go uruchamia sekwencję zadań tak samo jak dowolny inny komputer w kolekcji. Upewnij się, że wdrożenie systemu operacyjnego używa kolekcji zawierającej klientów zamierzone.  

     Zarządzać zachowaniem wdrożeń sekwencji zadań wysokiego ryzyka. Wdrożenie wysokiego ryzyka to wdrożenie, które jest instalowane automatycznie na kliencie i może mieć niepożądane skutki. Na przykład sekwencji zadań z celem wymagane, która wdraża system operacyjny. Aby zmniejszyć ryzyko niepożądanych wdrożeń o wysokim ryzyku, należy skonfigurować ustawienia weryfikacji wdrożenia. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   **Ilu komputerach można otrzymywać obrazu systemu operacyjnego, w tym samym czasie pojedynczego punktu dystrybucji?**  

     Aby oszacować liczbę potrzebnych punktów dystrybucji, należy wziąć pod uwagę następujące zmienne:  
       - Szybkość przetwarzania punktu dystrybucji
       - Prędkość dysku punktu dystrybucji
       - Dostępna przepustowość sieci
       - Rozmiar pakietu obrazu   
  
    Na przykład dowolnego innego serwera nie rozważ czynniki zasobu, maksymalną liczbę komputerów, które może przetworzyć pakietu obrazu 4 gigabajtów (GB) w ciągu jednej godziny w sieci Ethernet 100-megabita na sekundę jest 11 komputerów.  

    `100 megabits/sec = 12.5 megabytes/sec = 750 megabytes/min = 45 gigabytes/hour = 11 images @ 4 GB per image`  

    Jeśli zachodzi potrzeba wdrożenia systemu operacyjnego na konkretnej liczbie komputerów w określonym przedziale czasu, należy dokonać dystrybucji obrazu do odpowiedniej liczby punktów dystrybucji.  

-   **Czy mogę wdrożyć system operacyjny do punktu dystrybucji?**  

     System operacyjny można wdrożyć do punktu dystrybucji, ale obraz systemu operacyjnego musi być pobrany z innego punktu dystrybucji.  


###  <a name="BKMK_PXEDistributionPoint"></a> Konfigurowanie punktów dystrybucji do akceptowania żądań PXE  
 Aby wdrożyć systemy operacyjne klientów programu Configuration Manager, które żądania rozruchu środowiska PXE, należy skonfigurować co najmniej jeden punkt dystrybucji do akceptowania żądań PXE. Po skonfigurowaniu punktu dystrybucji ma odpowiadać na żądania rozruchu środowiska PXE i określa odpowiedniej akcji wdrażania do wykonania. Aby uzyskać więcej informacji, zobacz [zainstalować lub zmodyfikować punkt dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#pxe).  


###  <a name="BKMK_RamDiskTFTP"></a> Dostosuj rozmiar bloku i okna RamDisk TFTP w punktach dystrybucji z włączoną obsługą środowiska PXE  
Można dostosować rozmiar bloku i okna RamDisk TFTP dla punktów dystrybucji z włączoną obsługą środowiska PXE. Duży rozmiar bloku lub okna dostosowaną sieci, może spowodować pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu. Dostosowywanie rozmiaru bloku i okna RamDisk TFTP pozwalają na zoptymalizowanie ruchu TFTP przy użyciu środowiska PXE w celu spełnienia określonych wymagań sieciowych. Aby ustalić, jakie konfiguracja jest najbardziej wydajnym, należy przetestować dostosowane ustawienia w danym środowisku.  

-   **Rozmiar bloku TFTP**: Rozmiar bloku jest rozmiarem pakietów danych, które serwer wysyła do klienta pobierającego plik. Większy rozmiar bloku zezwala serwerowi na wysyłanie mniejszej liczby pakietów, co przekłada się na zmniejszenie obustronnych opóźnień między serwerem a klientem. Jednak duże blok o rozmiarze powodują fragmentowanie pakietów, które nie obsługują większość wdrożeń klienckich środowiska PXE.  

-   **Rozmiar okna TFTP**: TFTP wymaga pakietu z potwierdzeniem (ACK) dla każdego bloku danych, które są wysyłane. Serwer nie wyśle kolejnego bloku, dopóki nie odbierze pakietu ACK dla poprzedniego bloku. Dostosowywanie okien TFTP umożliwia zdefiniowanie liczby bloków danych potrzebnych do wypełnienia okna. Serwer wysyła bloki danych symetrycznie, dopóki okno nie zostanie wypełnione, a następnie klient wysyła pakiet ACK. Zwiększenie rozmiaru okna zmniejsza liczbę obustronnych opóźnień między klientem a serwerem i zmniejsza całkowity czas wymagany do pobrania obrazu rozruchowego.  
  


#### <a name="modify-the-ramdisk-tftp-window-size"></a>Zmodyfikuj rozmiar okna RamDisk TFTP  
Aby dostosować rozmiar okna RamDisk TFTP, Dodaj następujący klucz rejestru w punktach dystrybucji z włączoną obsługą środowiska PXE:  

  - **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
  - **Nazwa**: RamDiskTFTPWindowSize  
  - **Typ**: REG_DWORD  
  - **Wartość**: &lt;dostosowany rozmiar okna >  </br>
     Wartość domyślna to **1** (jeden blok danych będzie wypełniać okno)  

#### <a name="modify-the-ramdisk-tftp-block-size"></a>Zmodyfikuj rozmiar bloku RamDisk TFTP  
Aby dostosować rozmiar okna RamDisk TFTP, Dodaj następujący klucz rejestru w punktach dystrybucji z włączoną obsługą środowiska PXE:  

  - **Lokalizacja**: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\DP  
  - **Nazwa**: RamDiskTFTPBlockSize  
  - **Typ**: REG_DWORD  
  - **Wartość**: &lt;dostosowany rozmiar bloku >  </br>
     Wartość domyślna to **4096**.  


###  <a name="BKMK_DPMulticast"></a> Konfigurowanie punktów dystrybucji pod kątem obsługi multiemisji  
 Multiemisja to metoda optymalizacji sieci. Służy on w punktach dystrybucji w przypadku wielu klientów może pobierać ten sam obraz systemu operacyjnego, w tym samym czasie. Podczas korzystania z multiemisji, wielu komputerów może być jednocześnie pobierany obrazu systemu operacyjnego jest udostępniony w punkcie dystrybucji. Bez multiemisji punkt dystrybucji wysyła kopię danych do każdego klienta przez oddzielne połączenie. Aby uzyskać więcej informacji, zobacz [użyć multiemisji do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

 Przed wdrożeniem systemu operacyjnego należy skonfigurować punkt dystrybucji do obsługi multiemisji. Aby uzyskać więcej informacji, zobacz [zainstalować i skonfigurować punkty dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).


##  <a name="BKMK_StateMigrationPoints"></a> Punkt migracji stanu  
 Punkt migracji stanu przechowuje dane stanu użytkownika narzędzia USMT znajdują się na jednym komputerze, a następnie przywraca na innym komputerze. Jednak podczas przechwytywania ustawień użytkownika na potrzeby wdrożenia systemu operacyjnego na tym samym komputerze, na przykład wdrożenia, w którym odświeżeniu systemu Windows na komputerze docelowym, możesz wybrać, czy do przechowywania danych na tym samym komputerze przy użyciu twardych linków lub użyć punktu migracji stanu . Dla niektórych wdrożeń komputerów podczas tworzenia magazynu stanu programu Configuration Manager automatycznie tworzy skojarzenie między magazynem stanów i komputerem docelowym. Planując punkt migracji stanu, należy wziąć pod uwagę następujące czynniki:    

### <a name="user-state-size"></a>Rozmiar danych stanu użytkownika  
 Rozmiar danych stanu użytkownika bezpośrednio wpływa na magazyn dyskowy punktu migracji stanu oraz na wydajność sieci w czasie migracji. Należy uwzględnić rozmiar danych stanu użytkownika oraz liczbę komputerów, do których odbywa się migracja. Należy także wziąć pod uwagę, jakie ustawienia są migrowane z komputera. Na przykład jeśli **Moje dokumenty** folder już kopia zapasowa jest tworzona na serwerze, a następnie prawdopodobnie nie masz do migracji w ramach wdrożenia obrazu. Unikanie niepotrzebnych migracji zachowuje mniejszych całkowity rozmiar stanu użytkownika i zmniejsza wpływ, w przeciwnym razie mają go w sieci wydajność oraz Magazyn dyskowy punktu migracji stanu.  

### <a name="user-state-migration-tool"></a>Narzędzie do migracji stanu użytkowników  
 Aby przechwycić i przywrócić stan użytkownika podczas wdrażania systemu operacyjnego, należy korzystać z pakietu Narzędzie do migracji stanu użytkowników (USMT), który wskazuje pliki źródłowe narzędzia USMT. Menedżer konfiguracji automatycznie tworzy ten pakiet w konsoli programu Configuration Manager w **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **pakiety**. Configuration Manager używa narzędzia USMT 10 do przechwytywania stanu użytkownika z jednego systemu operacyjnego, a następnie przywróć ją na inny. Obejmuje narzędzia USMT 10, Windows Assessment and Deployment Kit (Windows ADK) dla systemu Windows 10.

 Opis różnych scenariuszy migracji dotyczących narzędzia USMT 10, zobacz [typowe scenariusze migracji](/windows/deployment/usmt/usmt-common-migration-scenarios) w dokumentacji systemu Windows.  

### <a name="retention-policy"></a>Zasady przechowywania  
 Podczas konfigurowania punktu migracji stanu, określ czas przechowywania danych stanu użytkownika, który jest przechowywany. Czas przechowywania danych na punkcie migracji stanu zależy od dwóch kwestii:  

-   Wpływ przechowywanych danych na magazyn dyskowy  

-   Potencjalny wymóg przechowywania danych przez pewien czas na wypadek ponownej migracji danych
  
  
Migracja stanu odbywa się w dwóch fazach: Przechwytywanie danych i przywracanie danych. Podczas przechwytywania dane stanu użytkownika są zbierane i zapisywane w punkcie migracji stanu. Podczas przywracania dane stanu użytkownika są pobierane z punktu migracji stanu i zapisywane na komputerze docelowym. Następnie zapisane dane są zwalniane w kroku **Zwolnij magazyn stanów** sekwencji zadań. Po uwolnieniu danych następuje włączenie licznika czasu przechowywania. Jeśli zostanie wybrana opcja usunięcia zmigrowanych danych, dane stanu użytkownika zostaną usunięte natychmiast po uwolnieniu. W przypadku wybrania opcji zachowania danych przez pewien czas dane zostaną usunięte po upływie tego czasu, liczonego od chwili uwolnienia danych. Już przechowywania możesz ustawić okres, więcej miejsca na dysku prawdopodobnie wymagają.  

### <a name="select-drive-to-store-user-state-migration-data"></a>Wybieranie dysku do zapisania danych migracji stanu użytkownika  
 Podczas konfigurowania punktu migracji stanu należy określić dysk serwera, na którym mają być przechowywane migrowane dane stanu użytkownika. Dysk można wybrać z listy. Niektóre dyski widoczne na liście mogą jednak być dyskami niezapisywalnymi, takimi jak napęd CD lub dysk niebędący udziałem sieciowym. Niektóre litery dysków mogą nie być mapowane do żadnych dysków na komputerze. Podczas konfigurowania punktu migracji stanu, określ zapisywalny, udostępniony dysk.  

### <a name="configure-a-state-migration-point"></a>Konfigurowanie punktu migracji stanu  
 Poniższe metody pozwalają skonfigurować punkt migracji stanu, tak aby przechowywać w nich dane o stanie użytkownika.  

-   Użyj **Kreatora tworzenia serwera systemu lokacji** , aby utworzyć nowy serwer systemu lokacji dla punktu migracji stanu.  

-   Użyj **Kreatora dodawania ról systemu lokacji** , aby dodać punkt migracji stanu do istniejącego serwera.  

 Korzystając z tych kreatorów, zostanie wyświetlony monit o podanie poniższych informacji dla punktu migracji stanu:  

-   Foldery do przechowywania danych o stanie użytkownika.  

-   Maksymalna liczba klientów, którzy mogą przechowywać dane w punkcie migracji stanu.  

-   Minimalna ilość wolnego miejsca dla punktu migracji stanu, w którym będą przechowywane dane o stanie użytkownika.  

-   Zasady usuwania dla nowej roli. Albo określić, czy dane stanu użytkownika zostaną usunięte natychmiast po ich przywróceniu na komputerze lub po określonej liczbie dni, po przywróceniu danych użytkownika na komputerze.  

-   Czy punkt migracji stanu odpowiada tylko na żądania przywrócenia danych stanu użytkownika. Włączenie tej opcji uniemożliwia użycie punktu migracji stanu do przechowywania danych o stanie użytkownika.  

 Aby uzyskać instrukcje dotyczące instalowania roli systemu lokacji, zobacz [Dodaj role systemu lokacji](../../core/servers/deploy/configure/add-site-system-roles.md).  
