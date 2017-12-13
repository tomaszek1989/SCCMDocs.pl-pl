---
title: "Zarządzanie sterownikami "
titleSuffix: Configuration Manager
description: "Aby zaimportować sterowniki urządzeń, sterowniki grupy w pakiety, przy użyciu katalogu sterowników programu Configuration Manager, a następnie dystrybucji tych pakietów do punktów dystrybucji."
ms.custom: na
ms.date: 01/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 84802d55-112e-4f7f-9a48-74a80d91a0f4
caps.latest.revision: "10"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f03f5d0e8c6d4653e25e50d615d5d50e00d9cda0
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="manage-drivers-in-system-center-configuration-manager"></a>Zarządzanie sterownikami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager udostępnia katalog sterowników, którego można użyć do zarządzania sterownikami urządzeń Windows w środowisku programu Configuration Manager. Katalogu sterowników można używać do importowania sterowników urządzeń do programu Configuration Manager, do grupowania ich w pakiety oraz do dystrybucji tych pakietów do punktów dystrybucji, w której będą dostępne podczas wdrażania systemu operacyjnego. Sterowników urządzeń można użyć w przypadku instalacji pełnego systemu operacyjnego na komputerze docelowym i instalowania systemu Windows PE za pomocą obrazu rozruchowego. Sterowniki urządzeń dla systemu Windows zawierają plik informacji instalatora (INF) oraz wszelkie dodatkowe pliki wymagane do obsługi urządzenia. Po wdrożeniu systemu operacyjnego programu Configuration Manager pobiera informacje o sprzęcie i platformie dotyczące urządzenia z pliku INF. Użyj następującego polecenia do zarządzania sterownikami w środowisku programu Configuration Manager.

##  <a name="BKMK_DriverCategories"></a> Kategorie sterowników urządzeń  
 Podczas importowania sterowników urządzeń można je przypisać do kategorii. Kategorie sterowników urządzeń ułatwiają grupowanie sterowników o podobnym przeznaczeniu w katalogu sterowników. Do jednej konkretnej kategorii można na przykład przypisać wszystkie sterowniki kart sieciowych. Następnie podczas tworzenia sekwencji zadań obejmującej krok [Automatycznie zastosuj sterowniki](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers) możesz określić specyficzną kategorię sterowników urządzeń. Programu Configuration Manager skanuje następnie sprzęt i i wybiera odpowiednie sterowniki z tej kategorii do umieszczenia w systemie dla Instalatora systemu Windows do użycia.  

##  <a name="BKMK_ManagingDriverPackages"></a> Pakiety sterowników  
 Możesz grupować podobne sterowniki urządzeń w pakiety, aby usprawnić wdrażanie systemu operacyjnego. Na przykład możesz utworzyć osobny pakiet sterowników dla każdego producenta komputerów w Twojej sieci. Pakiet sterowników można utworzyć w czasie importowania sterowników do katalogu sterowników w węźle **Pakiety sterowników** . Po utworzeniu pakietu sterowników, muszą być dystrybuowane do punktów dystrybucji, z których programu Configuration Manager komputery klienckie można zainstalować sterowników w razie potrzeby. Rozważ następujące opcje:  

-   W utworzonym pakiecie sterowników lokalizacja źródłowa pakietu musi wskazywać na pusty udział sieciowy, który nie jest używany przez inny pakiet sterowników, a dostawca programu SMS musi mieć przypisane uprawnienie do zapisu i do odczytu tej lokalizacji.  

-   Podczas dodawania sterowników urządzeń do pakietu sterowników, programu Configuration Manager kopiuje sterowniki do lokalizacji źródłowej pakietu sterowników. Do pakietu sterowników można dodawać tylko te sterowniki urządzeń, które zostały zaimportowane i są włączone w katalogu sterowników.  

-   Aby skopiować podzestaw sterowników urządzeń z istniejącego pakietu sterowników, utwórz nowy pakiet sterowników, dodaj podzestaw sterowników do nowego pakietu, a następnie przeprowadź dystrybucję nowego pakietu do punktu dystrybucji.  

 Użyj następujących sekcji, aby utworzyć pakiety sterowników i zarządzać nimi.  

###  <a name="CreatingDriverPackages"></a> Tworzenie pakietu sterowników  
 Aby utworzyć nowy pakiet sterowników, wykonaj czynności opisane w poniższej procedurze.  

> [!IMPORTANT]  
>  Do utworzenia pakietu sterowników jest wymagany pusty folder sieciowy, który nie jest używany przez inny pakiet sterowników. W większości przypadków musisz utworzyć nowy folder przed rozpoczęciem tej procedury.  

> [!NOTE]  
>  W przypadku korzystania z sekwencji zadań do instalowania sterowników utwórz pakiety sterowników zawierające mniej niż 500 sterowników urządzeń.  

 Aby utworzyć pakiet sterowników, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-a-driver-package"></a>Aby utworzyć pakiet sterowników  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Pakiety sterowników**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz pakiet sterowników**.  

4.  W polu **Nazwa** określ nazwę opisową pakietu sterowników.  

5.  W polu **Komentarz** wprowadź opcjonalnie opis pakietu sterowników. Upewnij się, że opis zawiera informacje dotyczące zawartości lub przeznaczenia pakietu sterowników.  

6.  W polu **Ścieżka** określ pusty folder źródłowy dla pakietu sterowników. Wprowadź ścieżkę do folderu źródłowego w formacie UNC (Universal Naming Convention). Każdy pakiet sterowników musi używać unikatowego folderu.  

    > [!IMPORTANT]  
    >  Konto serwera lokacji musi mieć uprawnienia **Odczyt** i **Zapis** do określonego folderu źródłowego.  

 Nowy pakiet nie zawiera żadnych sterowników. Następną czynnością jest dodanie sterowników do pakietu.  

 Jeżeli węzeł **Pakiety sterowników** zawiera kilka pakietów, można dodać do tego węzła foldery, aby podzielić pakiety na grupy logiczne.  

###  <a name="BKMK_PackageActions"></a> Dodatkowe akcje dla pakietów sterowników  
 Po wybraniu co najmniej jednego pakietu sterowników w węźle **Pakiety sterowników** są dostępne dodatkowe akcje w zakresie zarządzania pakietami sterowników. Dostępne są następujące akcje:  

|Akcja|Opis|  
|------------|-----------------|  
|**Utwórz wstępnie przygotowany plik zawartości**|Tworzy pliki, których można użyć do ręcznego zaimportowania zawartości i skojarzonych metadanych. Wstępnie przygotowanej zawartości należy używać w przypadku ograniczonej przepustowości sieci między serwerem lokacji a punktami dystrybucji, w których jest przechowywany pakiet sterowników.|  
|**Usuwanie**|Usuwa pakiet sterowników z węzła **Pakiety sterowników** .|  
|**Dystrybuuj zawartość**|Dystrybuuje pakiet sterowników do punktów dystrybucji, grup punktów dystrybucji oraz grup punktów dystrybucji skojarzonych z kolekcjami.|  
|**Zarządzaj kontami dostępu**|Dodaje, modyfikuje lub usuwa konta dostępu do pakietu sterowników.<br /><br /> Aby uzyskać więcej informacji dotyczących kont dostępu do pakietu, zobacz [konta używane w programie Configuration Manager](../../core/plan-design/hierarchy/accounts.md).|  
|**Przenieś**|Przenosi pakiet sterowników do innego folderu w węźle **Pakiety sterowników** .|  
|**Aktualizuj punkty dystrybucji**|Aktualizuje pakiet sterowników urządzenia we wszystkich punktach dystrybucji, w których pakiet jest przechowywany. Ta akcja umożliwia skopiowanie tylko zawartości zmienionej od jej ostatniej dystrybucji.|  
|**Właściwości**|Otwiera okno dialogowe **Właściwości** , w którym można sprawdzić i zmienić zawartość oraz właściwości sterownika urządzenia. Można na przykład zmienić nazwę i opis sterownika urządzenia, włączyć go oraz określić platformy, na których można uruchomić dany sterownik urządzenia.|  

##  <a name="BKMK_DeviceDrivers"></a> Sterowniki urządzeń  
 Możesz instalować sterowniki urządzeń na komputerach docelowych bez uwzględniania ich w obrazie systemu operacyjnego, który jest wdrażany. Configuration Manager udostępnia katalog sterowników, który zawiera odwołania do wszystkich sterowników urządzeń zaimportowanych do programu Configuration Manager. Katalog sterowników znajduje się w **Biblioteka oprogramowania** obszaru roboczego i składa się z dwóch węzłów: **Sterowniki** i **pakiety sterowników**. W węźle **Sterowniki** wyświetlają się wszystkie sterowniki zaimportowane do katalogu sterowników. Użyj tego węzła na potrzeby odnajdywania szczegółów każdego z zaimportowanych sterowników, modyfikowania sterowników w pakiecie sterowników lub obrazie rozruchowym, włączania lub wyłączania sterownika itd.  

###  <a name="BKMK_ImportDrivers"></a> Importowanie sterowników urządzeń do katalogu sterowników  
 Przed użyciem sterowników urządzeń w ramach wdrażania systemu operacyjnego należy je zaimportować do katalogu sterowników. Aby lepiej zarządzać sterownikami urządzeń, najlepiej zaimportować tylko te sterowniki, które są planowane do zainstalowania podczas wdrażania systemu operacyjnego. W katalogu sterowników można jednak przechowywać wiele wersji sterowników urządzeń, aby zapewnić łatwą metodę uaktualniania istniejących sterowników na wypadek zmiany wymogów sprzętowych sieci.  

 W ramach procesu importowania sterownika urządzenia programu Configuration Manager odczytuje dostawcy, klasy, wersji, podpisie, obsługiwanym sprzęcie oraz obsługiwane informacje platformy, które są skojarzone z danym urządzeniem. Domyślnie nazwa sterownika jest przypisywana na podstawie pierwszego obsługiwanego przez niego urządzenia sprzętowego. Później można jednak zmienić nazwę sterownika urządzenia. Lista obsługiwanych platform powstaje na podstawie informacji w pliku INF sterownika. Dokładność tych informacji może się różnić, dlatego po zaimportowaniu sterownika urządzenia do katalogu sterowników należy ręcznie sprawdzić, czy jest on obsługiwany.  

 Po zaimportowaniu sterowników urządzeń do katalogu możesz dodać je do pakietów sterowników lub pakietów obrazów rozruchowych.  

> [!IMPORTANT]  
>  Sterowników urządzeń nie można zaimportować bezpośrednio do podfolderu w węźle **Sterowniki** . Aby zaimportować sterownik urządzenia do podfolderu, najpierw należy go zaimportować do węzła **Sterowniki** , a następnie przenieść ten sterownik do podfolderu.  

 Aby zaimportować sterowniki urządzeń systemu Windows, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-import-windows-device-drivers-into-the-driver-catalog"></a>Aby zaimportować sterowniki urządzeń systemu Windows do katalogu sterowników  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sterowniki**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Importuj sterownik** , aby uruchomić **Kreatora importowania nowego sterownika**.  

4.  Na stronie **Lokalizowanie sterownika** określ następujące opcje, a następnie kliknij przycisk **Dalej**:  

    -   **Importuj wszystkie sterowniki w następującej ścieżce sieciowej (UNC)**: Aby zaimportować wszystkie sterowniki urządzeń, które znajdują się w określonym folderze, określ ścieżkę sieciową do folderu sterowników urządzeń. Na przykład:  **\\\nazwa_serwera\folder**.  

        > [!NOTE]  
        >  Proces importowania wszystkich sterowników może zająć trochę czasu, jeśli istnieje wiele folderów i wiele plików sterowników (inf).  

    -   **Importuj wybrany sterownik**: Aby zaimportować wybrany sterownik z folderu, określ ścieżkę sieciową (UNC) do sterownika urządzenia systemu Windows. Plik INF lub masowej magazynu pliku Txtsetup.oem sterownika.  

    -   **Wybierz opcję dla zduplikowanych sterowników**: Wybierz, jak program Configuration Manager ma zarządzać kategoriami sterowników po zaimportowaniu dysku zduplikowane urządzenie.  

    > [!IMPORTANT]  
    >  Podczas importowania sterowników serwer lokacji musi mieć uprawnienie **Odczyt** w danym folderze. W przeciwnym razie importowanie zakończy się niepowodzeniem.  

5.  Na stronie **Szczegóły sterownika** określ następujące opcje, a następnie kliknij przycisk **Dalej**:  

    -   **Ukryj sterowniki, które nie należą do klasy sieci lub magazynu (na potrzeby obrazów rozruchowych)**: Użyj tego ustawienia, aby wyświetlić tylko sterowniki magazynów i sieci oraz ukryć inne sterowniki, które nie są zwykle wymagane przez obrazy rozruchowe, takie jak sterownik wideo lub sterownik modemu.  

    -   **Ukryj sterowniki, które nie są podpisane cyfrowo**: To ustawienie umożliwia ukrycie sterowników, które nie są podpisane cyfrowo.  

    -   Wybierz z listy sterowniki, które mają zostać zaimportowane do katalogu sterowników.  

    -   **Włącz te sterowniki i Zezwól komputerom na ich instalację**: Wybierz to ustawienie, aby umożliwić komputerom zainstalowanie sterowników urządzeń. To pole wyboru jest domyślnie zaznaczone.  

        > [!IMPORTANT]  
        >  Jeżeli sterownik urządzenia powoduje problem, lub w celu wstrzymania instalacji sterownika urządzenia, można wyłączyć ten sterownik, usuwając zaznaczenie pola wyboru **Włącz te sterowniki i zezwól komputerom na ich instalację** . Sterowniki można również wyłączyć po ich zaimportowaniu.  

    -   Aby przypisać sterowniki urządzeń do kategorii administracyjnej w celu ich filtrowania, np. wg kategorii „Komputery stacjonarne” lub „Komputery przenośne”, kliknij przycisk **Kategorie** i wybierz istniejącą kategorię lub utwórz nową. Kategorie można również przypisywać w celu skonfigurowania sterowników urządzeń stosowanych w ramach wdrożenia przez krok sekwencji zadań [Automatycznie zastosuj sterowniki](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers).  

6.  Na stronie **Dodawanie sterownika do pakietów** wybierz, czy dodać sterowniki do pakietu, a następnie kliknij przycisk **Dalej**. Uwzględnij następujące zagadnienia, aby dodać sterowniki do pakietu:  

    -   Wybierz pakiety sterowników używane do rozpraszania sterowników urządzeń.  

         Opcjonalnie kliknij przycisk **Nowy pakiet** , aby utworzyć nowy pakiet sterowników. W przypadku tworzenia nowego pakietu sterowników należy określić udział sieciowy, który nie jest używany przez inne pakiety sterowników.  

    -   Jeśli pakiet został już rozesłany do punktów dystrybucji, kliknij przycisk **Tak** w oknie dialogowym, aby zaktualizować obrazy rozruchowe w punktach dystrybucji. Nie można używać sterowników urządzeń dopóki nie zostaną rozproszone do punktów dystrybucji. Jeśli klikniesz przycisk **Nie**, wówczas musisz uruchomić akcję **Zaktualizuj punkt dystrybucji** — dopiero wówczas obraz rozruchowy będzie zawierał zaktualizowane sterowniki. Jeśli pakiet sterowników nigdy nie został rozesłany, należy kliknąć opcję **Dystrybuuj zawartość** w węźle **Pakiety sterowników** .  

7.  Na stronie **Dodawanie sterownika do obrazów rozruchowych** wybierz, czy dodać sterowniki urządzeń do istniejących obrazów rozruchowych, a następnie kliknij przycisk **Dalej**. W przypadku wybrania obrazu rozruchowego uwzględnij następujące zagadnienia:  

    > [!NOTE]  
    >  Najlepszą metodą postępowania w przypadku scenariuszy obejmujących wdrożenie systemu operacyjnego jest dodanie do obrazów rozruchowych tylko sterowników urządzeń sieciowych i pamięci masowej.  

    -   Kliknij przycisk **Tak** w oknie dialogowym, aby zaktualizować obrazy rozruchowe w punktach dystrybucji. Nie można używać sterowników urządzeń dopóki nie zostaną rozproszone do punktów dystrybucji. Jeśli klikniesz przycisk **Nie**, wówczas musisz uruchomić akcję **Zaktualizuj punkt dystrybucji** — dopiero wówczas obraz rozruchowy będzie zawierał zaktualizowane sterowniki. Jeśli pakiet sterowników nigdy nie został rozesłany, należy kliknąć opcję **Dystrybuuj zawartość** w węźle **Pakiety sterowników** .  

    -   Configuration Manager wyświetli ostrzeżenie, jeśli architektura co najmniej jednego sterownika nie jest zgodna z architekturą wybranych obrazów rozruchowych. Jeśli występuje niezgodność, kliknij przycisk **OK** i wróć do strony **Szczegóły sterownika** , aby wyczyścić sterowniki, które nie są zgodne z architekturą wybranego obrazu rozruchowego. Na przykład w przypadku wybrania obrazu rozruchowego x64 i x86 wszystkie sterowniki muszą obsługiwać obie architektury. Jeśli wybierzesz obraz rozruchowy x64, wszystkie sterowniki muszą obsługiwać architekturę x64.  

        > [!NOTE]  
        >  -   Architektura jest oparta na architekturze zgłoszonej w pliku INF dostarczonym przez producenta.  
        > -   Jeśli sterownik zgłasza, że obsługuje obie architektury, wówczas można go zaimportować do dowolnego obrazu rozruchowego.  

    -   Configuration Manager wyświetli ostrzeżenie, jeśli musisz dodać sterowniki urządzeń, które nie są sieci lub magazynu sterowników do obrazu rozruchowego, ponieważ w większości przypadków nie są niezbędne dla obrazu rozruchowego. Kliknij przycisk **Tak** , aby dodać sterowniki do obrazu rozruchowego, lub przycisk **Nie** , aby wrócić i zmodyfikować wybór sterowników.  

    -   Configuration Manager wyświetli ostrzeżenie, jeśli jeden lub więcej z wybranych sterowników nie jest poprawnie cyfrowo podpisany. Kliknij przycisk **Tak** , aby kontynuować, a następnie kliknij przycisk **Nie** , aby wrócić i zmienić wybór sterownika.  

8.  Ukończ pracę kreatora.  

###  <a name="BKMK_ModifyDriverPackage"></a> Zarządzanie sterownikami urządzeń w pakiecie sterowników  
 Aby zmodyfikować pakiety sterowników i obrazy rozruchowe, wykonaj czynności opisane w poniższych procedurach. Aby dodać lub usunąć sterowniki urządzeń, zlokalizuj je w węźle **Sterowniki** , a następnie edytuj pakiety lub obrazy rozruchowe, z którymi wybrane sterowniki są skojarzone.  

#### <a name="to-modify-the-device-drivers-in-a-driver-package"></a>Modyfikowanie sterowników urządzeń w pakiecie sterowników  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sterowniki**.  

3.  W węźle **Sterowniki** wybierz sterowniki urządzeń, które mają zostać dodane do pakietu sterowników.  

4.  Na karcie **Narzędzia główne** w grupie **Sterownik** kliknij przycisk **Edytuj**, a następnie kliknij przycisk **Pakiety sterowników**.  

5.  Aby dodać sterownik urządzenia, zaznacz pola wyboru przy pakietach sterowników, do których mają zostać dodane odpowiednie sterowniki. Aby usunąć sterownik urządzenia, usuń zaznaczenia pól wyboru przy pakietach sterowników, z których mają zostać usunięte sterowniki.  

     W przypadku dodawania sterowników urządzeń skojarzonych z pakietami sterowników można opcjonalnie utworzyć nowy pakiet, klikając przycisk **Nowy pakiet**. Zostanie wyświetlone okno dialogowe **Nowy pakiet sterowników** .  

6.  Jeśli pakiet został już rozesłany do punktów dystrybucji, kliknij przycisk **Tak** w oknie dialogowym, aby zaktualizować obrazy rozruchowe w punktach dystrybucji. Nie można używać sterowników urządzeń dopóki nie zostaną rozproszone do punktów dystrybucji. Jeśli klikniesz przycisk **Nie**, wówczas musisz uruchomić akcję **Zaktualizuj punkt dystrybucji** — dopiero wówczas obraz rozruchowy będzie zawierał zaktualizowane sterowniki. Jeśli pakiet sterowników nigdy nie został rozesłany, należy kliknąć opcję **Dystrybuuj zawartość** w węźle **Pakiety sterowników** . Zanim sterowniki staną się dostępne, musisz zaktualizować pakiet sterownika w punktach dystrybucji.  

     Kliknij przycisk **OK**.  

###  <a name="BKMK_ManageDriversBootImage"></a> Zarządzanie sterownikami urządzeń w obrazie rozruchowym  
 Do obrazów rozruchowych można dodawać sterowniki urządzeń dla systemu Windows, które zostały zaimportowane do katalogu sterowników. Podczas dodawania sterowników urządzeń do obrazu rozruchowego należy przestrzegać poniższych wytycznych:  

-   Do obrazów rozruchowych należy dodawać tylko sterowniki pamięci masowych i kart sieciowych, ponieważ sterowniki innych typów nie są zwykle wymagane. Sterowniki, które nie są wymagane, niepotrzebnie zwiększają rozmiar obrazu rozruchowego.  

-   Do obrazów rozruchowych należy dodawać tylko sterowniki urządzeń dla systemu Windows 10, ponieważ wymagana wersja środowiska Windows PE jest oparta na systemie Windows 10.  

-   Należy się upewnić, że wersja używanego sterownika urządzenia odpowiada architekturze obrazu rozruchowego.  Nie wolno dodawać sterowników urządzeń typu x86 do obrazu rozruchowego typu x64.  

 Użyj następującej procedury, aby dodać lub usunąć sterowniki urządzeń w obrazie rozruchowym.  

#### <a name="to-modify-the--device-drivers-associated-with-a-boot-image"></a>Modyfikowanie sterowników urządzeń skojarzonych z obrazem rozruchowym  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sterowniki**.  

3.  W węźle **Sterowniki** wybierz sterowniki urządzeń, które mają zostać dodane do pakietu sterowników.  

4.  Na karcie **Narzędzia główne** w grupie **Sterownik** kliknij przycisk **Edytuj**, a następnie kliknij przycisk **Obrazy rozruchowe**.  

5.  Aby dodać sterownik urządzenia, zaznacz pole wyboru przy obrazie rozruchowym, do którego mają zostać dodane odpowiednie sterowniki. Aby usunąć sterownik urządzenia, usuń zaznaczenie pola wyboru przy obrazie rozruchowym, z którego mają zostać usunięte sterowniki.  

6.  Aby nie aktualizować punktów dystrybucji, w których zapisano obraz rozruchowy, usuń zaznaczenie pola wyboru **Aktualizuj punkty dystrybucji po zakończeniu** . Domyślnie punkty dystrybucji są aktualizowane w ramach aktualizacji obrazu rozruchowego.  

     Kliknij przycisk **OK** i rozważ następujące opcje:  

    -   Kliknij przycisk **Tak** w oknie dialogowym, aby zaktualizować obrazy rozruchowe w punktach dystrybucji. Nie można używać sterowników urządzeń dopóki nie zostaną rozproszone do punktów dystrybucji. Jeśli klikniesz przycisk **Nie**, wówczas musisz uruchomić akcję **Zaktualizuj punkt dystrybucji** — dopiero wówczas obraz rozruchowy będzie zawierał zaktualizowane sterowniki. Jeśli pakiet sterowników nigdy nie został rozesłany, należy kliknąć opcję **Dystrybuuj zawartość** w węźle **Pakiety sterowników** .  

    -   Configuration Manager wyświetli ostrzeżenie, jeśli architektura co najmniej jednego sterownika nie jest zgodna z architekturą wybranych obrazów rozruchowych. Jeśli występuje niezgodność, kliknij przycisk **OK** i wróć do strony **Szczegóły sterownika** , aby wyczyścić sterowniki, które nie są zgodne z architekturą wybranego obrazu rozruchowego. Na przykład w przypadku wybrania obrazu rozruchowego x64 i x86 wszystkie sterowniki muszą obsługiwać obie architektury. Jeśli wybierzesz obraz rozruchowy x64, wszystkie sterowniki muszą obsługiwać architekturę x64.  

        > [!NOTE]  
        >  -   Architektura jest oparta na architekturze zgłoszonej w pliku INF dostarczonym przez producenta.  
        > -   Jeśli sterownik zgłasza, że obsługuje obie architektury, wówczas można go zaimportować do dowolnego obrazu rozruchowego.  

    -   Configuration Manager wyświetli ostrzeżenie, jeśli musisz dodać sterowniki urządzeń, które nie są sieci lub magazynu sterowników do obrazu rozruchowego, ponieważ w większości przypadków nie są niezbędne dla obrazu rozruchowego. Kliknij przycisk **Tak** , aby dodać sterowniki do obrazu rozruchowego, lub przycisk **Nie** , aby wrócić i zmodyfikować wybór sterowników.  

    -   Configuration Manager wyświetli ostrzeżenie, jeśli jeden lub więcej z wybranych sterowników nie jest poprawnie cyfrowo podpisany. Kliknij przycisk **Tak** , aby kontynuować, a następnie kliknij przycisk **Nie** , aby wrócić i zmienić wybór sterownika.  

7.  Kliknij przycisk **OK**.  

###  <a name="BKMK_DriverActions"></a> Dodatkowe akcje dla sterowników urządzeń  
 Po wybraniu co najmniej jednego sterownika urządzenia w węźle **Sterowniki** są dostępne dodatkowe akcje w zakresie zarządzania sterownikami urządzeń. Dostępne są następujące akcje:  

|Akcja|Opis|  
|------------|-----------------|  
|**Kategoryzuj**|Czyści, zarządza lub ustawia kategorie administracyjne wybranych sterowników urządzeń.|  
|**Usuwanie**|Usuwa sterownik urządzenia z węzła **Sterowniki** , a także ze skojarzonych punktów dystrybucji.|  
|**Wyłącz**|Zabrania instalowania sterownika urządzenia. Sterowniki urządzeń można tymczasowo wyłączyć, aby komputery klienckie programu Configuration Manager i sekwencji zadań nie może je zainstalować w przypadku wdrażania systemów operacyjnych. **Uwaga:**  Akcja Wyłącz zapobiega wyłącznie sterowniki instalacji za pomocą kroku sekwencji zadań automatycznie Zastosuj sterowniki.|  
|**Włączenie**|Umożliwia klientów programu Configuration Manager i sekwencji zadań instalowania sterownika urządzenia podczas wdrażania systemu operacyjnego.|  
|**Przenieś**|Przenosi sterownik urządzenia do innego folderu w węźle **Sterowniki** .|  
|**Właściwości**|Otwiera okno dialogowe **Właściwości** , w którym można sprawdzić i zmienić właściwości sterownika urządzenia. Można na przykład zmienić nazwę i opis sterownika urządzenia, włączyć go oraz określić platformy, na których można uruchomić dany sterownik urządzenia.|  

##  <a name="BKMK_TSDrivers"></a> Użyj sekwencji zadań, aby zainstalować sterowniki urządzeń  
 Wdrażanie systemu operacyjnego można zautomatyzować za pomocą sekwencji zadań. Każdy krok sekwencji zadań może wykonywać konkretną akcję, na przykład instalowanie sterownika urządzenia. Aby zainstalować sterowniki urządzeń podczas wdrażania systemu operacyjnego, można użyć dwóch poniższych kroków sekwencji zadań:  

-   [Automatycznie Zastosuj sterowniki](../understand/task-sequence-steps.md#BKMK_AutoApplyDrivers): Ten krok pozwala automatycznie dopasować i zainstalować sterowniki urządzeń w ramach wdrożenia systemu operacyjnego. Krok sekwencji zadań można skonfigurować tak, aby instalował tylko sterownik najlepiej dopasowany do wykrytego urządzenia sprzętowego albo instalował wszystkie zgodne sterowniki, a następnie umożliwił Instalatorowi systemu Windows wybranie najlepszego z nich. Ponadto można określić kategorię sterowników urządzeń, aby ograniczyć liczbę sterowników dostępnych w tym kroku.  

-   [Zastosuj pakiet sterowników](../understand/task-sequence-steps.md#BKMK_ApplyDriverPackage): Ten krok pozwala udostępnić wszystkie sterowniki urządzeń w konkretnym pakiecie sterowników dla Instalatora systemu Windows. Instalator systemu Windows wyszuka wymagane sterowniki urządzeń we wskazanych pakietach sterowników. Podczas tworzenia autonomicznego nośnika musisz użyć tego kroku, aby zainstalować sterowniki urządzeń.  

 Podczas korzystania z tych kroków sekwencji zadań można także określić, w jaki sposób sterowniki urządzeń są instalowane na komputerze, na którym jest wdrażany system operacyjny. Aby uzyskać więcej informacji, zobacz [Zarządzanie sekwencjami zadań do automatyzowania zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md).  

##  <a name="BKMK_InstallingDeviceDiriversTS"></a> Użyj sekwencji zadań, aby zainstalować sterowniki urządzeń na komputerach  
 Aby zainstalować sterowniki urządzeń w ramach wdrażania systemu operacyjnego, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="use-a-task-sequence-to-install-device-drivers"></a>Instalowanie sterowników urządzeń za pomocą sekwencji zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  W węźle **Sekwencje zadań** wybierz sekwencję zadań instalowania sterownika urządzenia, która ma zostać zmodyfikowana, a następnie kliknij przycisk **Edytuj**.  

4.  Przejdź do lokacji, do której chcesz dodać kroki **Sterownik** , kliknij przycisk **Dodaj**i wybierz polecenie **Sterowniki**.  

5.  Jeśli sekwencja zadań ma instalować wszystkie sterowniki urządzeń lub wyłącznie z określonych specyficznych kategorii, dodaj krok **Automatycznie zastosuj sterowniki** . Określ opcje kroku na karcie **Właściwości** i wprowadź wszystkie jego warunki na karcie **Opcje** .  

     Jeśli sekwencja zadań ma instalować tylko sterowniki urządzenia z określonego pakietu, dodaj krok **Zastosuj pakiet sterowników** . Określ opcje kroku na karcie **Właściwości** i wprowadź wszystkie jego warunki na karcie **Opcje** .  

    > [!IMPORTANT]  
    >  Możesz wybrać pozycję **Wyłącz ten krok** na karcie **Opcje** , aby wyłączyć krok w celu rozwiązania problemu z sekwencją zadań.  

6.  Aby zapisać sekwencję zadań, kliknij przycisk **OK** .  

 Aby uzyskać więcej informacji o tworzeniu sekwencji zadań w celu zainstalowania systemu operacyjnego, zobacz [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](../deploy-use/create-a-task-sequence-to-install-an-operating-system.md).  

##  <a name="BKMK_DriverReports"></a> Raporty zarządzania sterownikami  
 Aby sprawdzić ogólne informacje o sterownikach urządzeń w katalogu sterowników, można skorzystać z szeregu raportów dostępnych w kategorii raportów **Zarządzanie sterownikiem** . Aby uzyskać więcej informacji o raportach zobacz [raportowania](../../core/servers/manage/reporting.md).
