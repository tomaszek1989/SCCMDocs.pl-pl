---
title: "Zarządzanie punktami dystrybucji | Dokumentacja firmy Microsoft"
description: "Udostępniać zawartość (pliki i oprogramowania), która wdrażane do urządzeń i użytkowników przy użyciu punktów dystrybucji. Poniżej przedstawiono sposób zainstalować i skonfigurować je."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebafaf9-b3d5-4a0f-9ee5-685758c037a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8728d9f2ae63282a8f58b20105e488fb1a5ef55b
ms.openlocfilehash: 4c94e4de5bbfe621492e8682c9424a48eb38196d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="install-and-configure-distribution-points-for-system-center-configuration-manager"></a>Instalowanie i konfigurowanie punktów dystrybucji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*
 
Zainstaluj punktów dystrybucji programu System Center Configuration Manager, aby obsługiwać zawartość (pliki i oprogramowania), wdrażanego na urządzeniach i użytkowników. Można również utworzyć dystrybucji grupy punktów, które upraszczają, jak zarządzać punktami dystrybucji i sposób dystrybucji zawartości do punktów dystrybucji.  

 Gdy użytkownik *instalacji nowego punktu dystrybucji* (przy użyciu Kreatora instalacji) lub *Zarządzanie właściwościami istniejący punkt dystrybucji* (, edytując właściwości punktu dystrybucji), można skonfigurować większość ustawień punktu dystrybucji. Kilka ustawienia są dostępne tylko wtedy, gdy użytkownik jest instalowanie lub edycji, ale nie obu:  

-   Ustawienia, które są dostępne tylko podczas instalowania punktu dystrybucji:  

    -   **Menedżer konfiguracji instalację usług IIS na komputerze punktu dystrybucji**

    -   **Skonfiguruj ustawienia miejsca na dysku dla punktu dystrybucji**  

-   Ustawienia, które są dostępne tylko podczas edycji właściwości punktu dystrybucji:  

    -   **Zarządzanie relacjami grupy punktu dystrybucji**  

    -   **Wyświetl zawartość wdrożona w punkcie dystrybucji**  

    -   **Konfigurowanie limitów szybkości transferu danych do punktów dystrybucji**  

    -   **Harmonogramy można konfigurować do przesyłania danych do punktów dystrybucji**  

##  <a name="bkmk_install"></a>Zainstalowanie punktu dystrybucji  
 Aby zawartość można udostępnić komputerom klienckim, należy wyznaczyć serwer systemu lokacji jako punkt dystrybucji. Można dodać rolę lokacji punktu dystrybucji do nowego serwera systemu lokacji lub dodać rolę lokacji do istniejącego serwera systemu lokacji.  

 Po zainstalowaniu nowego punktu dystrybucji, można użyć Kreatora instalacji, który przeprowadzi Cię przez dostępne ustawienia. Przed rozpoczęciem należy uwzględnić następujące kwestie:  

-   Musi mieć następujące uprawnienia zabezpieczeń w celu utworzenia i skonfigurowania punktu dystrybucji:  

    -   **Odczyt** dla **punktu dystrybucji** obiektu  

    -   **Kopiuj do punktu dystrybucji** dla **punktu dystrybucji** obiektu  

    -   **Modyfikowanie** dla **witryny** obiektu  

    -   **Zarządzanie certyfikatami wdrożenia systemu operacyjnego** dla **witryny** obiektu  

-   Internet Information Services (IIS) należy zainstalować na serwerze, który będzie hostem punktu dystrybucji. Podczas instalowania roli systemu lokacji programu Configuration Manager można zainstalować i skonfigurować usługi IIS.  

Użyj poniższych procedur podstawowe zainstalować lub Zmiana punktu dystrybucji. Szczegółowe informacje na temat dostępnych opcji konfiguracji, zobacz [konfigurowania punktu dystrybucji](#bkmk_configs) tego tematu.  

#### <a name="to-install-a-distribution-point"></a>Aby zainstalować punkt dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

2.  Dodaj rolę systemu lokacji punktu dystrybucji do nowej lub istniejącej lokacji serwera systemu:  

    -   **Nowy serwer systemu lokacji**: Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz serwer systemu lokacji**. Otworzy się Kreator tworzenia serwera systemu lokacji.  

    -   **Istniejący serwer systemu lokacji**: Wybierz serwer, w którym chcesz zainstalować rolę systemu lokacji punktu dystrybucji. Po wybraniu serwera w okienku wyników zostanie wyświetlona lista ról systemu lokacji, które są już zainstalowane na serwerze.  

         Na **Home** w karcie **serwera** grupy, wybierz **Dodaj rolę systemu lokacji**. Otworzy się Kreator dodawania ról systemu lokacji.  

3.  Na stronie **Ogólne** określ ustawienia ogólne serwera systemu lokacji. Podczas dodawania punktu dystrybucji do istniejącego serwera systemu lokacji, należy sprawdzić wcześniej skonfigurowane wartości.  

4.  Na **Wybór roli systemu** wybierz **punktu dystrybucji** z listy dostępnych ról, a następnie wybierz **dalej**.  

5.  Na kolejnych stronach kreatora, zapoznaj się z informacjami w [konfigurowania punktu dystrybucji](#bkmk_configs) sekcji.  

     Na przykład, jeśli chcesz zainstalować punkt dystrybucji jako ściągający punkt dystrybucji, możesz wybrać **Włącz ten punkt dystrybucji do ściągania zawartości z innych punktów dystrybucji** , a następnie wprowadź dodatkowe konfiguracje, które wymagają ściągających punktów dystrybucji.  

6.  Po zakończeniu pracy kreatora do serwera systemu lokacji zostanie dodana roli lokacji punktu dystrybucji.  

#### <a name="to-change-a-distribution-point"></a>Aby zmienić punkt dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** >  **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, który chcesz skonfigurować.  

2.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

3.  Informacje zawarte w [konfigurowania punktu dystrybucji](#bkmk_configs) sekcja podczas edycji właściwości punktu dystrybucji.  

4.  Po wprowadzeniu zmian, które chcesz zapisać ustawienia i zamknąć właściwości punktu dystrybucji.  

##  <a name="bkmk_manage"></a>Zarządzanie grupami punktów dystrybucji  
 Grupy punktów dystrybucji umożliwiają logiczne grupowanie punktów dystrybucji zawartości. Te grupy umożliwia zarządzanie i monitorowanie zawartości z centralnej lokalizacji punktów dystrybucji, obejmującej wiele lokacji. Należy uwzględnić następujące czynności:

-   Można dodać jeden lub więcej punktów dystrybucji z dowolnej lokacji w hierarchii, do grupy punktów dystrybucji.  

-   Można dodać punkt dystrybucji do więcej niż jednej grupy punktów dystrybucji.  

-   Podczas dystrybucji zawartości do grupy punktów dystrybucji programu Configuration Manager przesyła zawartość do wszystkich punktów dystrybucji, które należą do grupy punktów dystrybucji.  

-   Po dodaniu punktu dystrybucji do grupy punktów dystrybucji po początkowej dystrybucji zawartości programu Configuration Manager automatycznie przesyła zawartość do nowego członka punktu dystrybucji.  

-   Kolekcja można skojarzyć z grupą punktów dystrybucji. Podczas dystrybucji zawartości do tej kolekcji programu Configuration Manager określa grupy punktów dystrybucji, które są skojarzone z tą kolekcją. Zawartość jest dystrybuowana do wszystkich punktów dystrybucji, które należą do tych grup punktów dystrybucji.  

    > [!NOTE]  
    >  Po dystrybucji zawartości do kolekcji, jeśli następnie skojarzyć kolekcję z grupą punktów dystrybucji, należy ponownie przesłać zawartość do kolekcji przed rozesłaniem zawartości do nowej grupy punktów dystrybucji.  

#### <a name="to-create-and-configure-a-new-distribution-point-group"></a>Aby utworzyć i skonfigurować nową grupę punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **grupy punktów dystrybucji**.  

2.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz grupę**.  

3.  Wprowadź nazwę i opis grupy punktów dystrybucji.  

4.  Na **kolekcji** , wybierz **Dodaj**, wybierz kolekcje, które chcesz skojarzyć z grupą punktów dystrybucji, a następnie wybierz **OK**.  

5.  Na **członków** , wybierz **Dodaj**, wybierz punkty dystrybucji, które chcesz dodać jako członków grupy punktów dystrybucji, a następnie wybierz **OK**.  

6.  Wybierz **OK** Aby utworzyć grupę punktów dystrybucji.  

#### <a name="to-add-distribution-points-and-associate-collections-with-an-existing-distribution-point-group"></a>Aby dodać punkty dystrybucji i skojarzyć kolekcje z istniejącą grupę punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **grupy punktów dystrybucji**.  

2.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

3.  Na **kolekcji** , wybierz **Dodaj** aby wybrać kolekcje, które chcesz skojarzyć z grupą punktów dystrybucji, a następnie wybierz **OK**.  

4.  Na **członków** , wybierz **Dodaj** aby wybrać punkty dystrybucji, które chcesz dodać jako członków grupy punktów dystrybucji, a następnie wybierz **OK**.  

5.  Wybierz **OK** zapisać zmiany w grupie punktów dystrybucji.  

#### <a name="to-add-selected-distribution-points-to-a-new-distribution-point-group"></a>Aby dodać wybrane punkty dystrybucji do nowej grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **punktów dystrybucji**, a następnie wybierz punkty dystrybucji, które chcesz dodać do nowej grupy punktów dystrybucji.  

2.  Na **Home** w karcie **punktu dystrybucji** rozwiń węzeł **Dodaj wybrane elementy**, a następnie wybierz **Dodaj wybrane elementy do nowej grupy punktów dystrybucji**.  

3.  Wprowadź nazwę i opis grupy punktów dystrybucji.  

4.  Na **kolekcji** , wybierz **Dodaj** aby wybrać kolekcje, które chcesz skojarzyć z grupą punktów dystrybucji, a następnie wybierz **OK**.  

5.  Na **członków** Potwierdź, że program Configuration Manager, aby dodać punkty dystrybucji znajdujące się jako członków grupy punktów dystrybucji. Wybierz **Dodaj** dodać punkty dystrybucji, a następnie wybierz polecenie **OK**.  

6.  Wybierz **OK** Aby utworzyć grupę punktów dystrybucji.  

#### <a name="to-add-selected-distribution-points-to-existing-distribution-point-groups"></a>Aby dodać wybrane punkty dystrybucji do istniejących grup punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **punktów dystrybucji**, a następnie wybierz punkty dystrybucji, które chcesz dodać do nowej grupy punktów dystrybucji.  

2.  Na **Home** w karcie **punktu dystrybucji** rozwiń węzeł **Dodaj wybrane elementy**, a następnie wybierz **Dodaj wybrane elementy do istniejących grup punktów dystrybucji**.  

3.  W **dostępne grupy punktów dystrybucji**, wybierz grupy punktów dystrybucji, do których zostaną dodane wybrane punkty dystrybucji jako elementy członkowskie, a następnie wybierz **OK**.  

##  <a name="bkmk_configs"></a>Skonfiguruj punkt dystrybucji  
 Poszczególne punkty dystrybucji obsługują szereg różnych konfiguracji. Jednak nie wszystkie typy punkt dystrybucji obsługuje wszystkie konfiguracje. Na przykład punkty dystrybucji w chmurze nie obsługują wdrożeniami zawartości z obsługą środowiska PXE lub multiemisji. Informacje o ograniczeniach określonych można znaleźć w następujących tematach:  

-   [Użycia punktu dystrybucji w chmurze z System Center Configuration Manager](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)  

-   [Użyj ściągający punkt dystrybucji z System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)  

W poniższych sekcjach opisano konfiguracje, które można wybrać podczas instalacji nowego punktu dystrybucji lub edytowania właściwości istniejący punkt dystrybucji.  

### <a name="general"></a>Ogólne  
 Skonfiguruj ogólne ustawienia punktu dystrybucji:  

-   **Instalowanie i konfigurowanie usług IIS, jeśli jest to wymagane przez program Configuration Manager**: Wybierz to ustawienie, aby umożliwić programowi Configuration Manager, instalowanie i konfigurowanie usług IIS na serwerze, jeśli nie jest już zainstalowany. Usługi IIS muszą być zainstalowane we wszystkich punktach dystrybucji. Jeśli usługi IIS nie jest zainstalowany na serwerze i to ustawienie nie zostanie wybrane, należy zainstalować usługi IIS, aby umożliwić pomyślne zainstalowanie punktu dystrybucji.  

    > [!NOTE]  
    >  Ta opcja jest dostępna tylko w przypadku instalowania nowego punktu dystrybucji.  

- **Włącz i skonfiguruj usługi BranchCache dla tego punktu dystrybucji**: Wybierz to ustawienie, aby umożliwić programowi Configuration Manager, skonfiguruj usługi Windows BranchCache na serwerze punktu dystrybucji. Aby uzyskać więcej informacji o korzystaniu z usługi Windows BranchCache z System Center Configuration Manager, zobacz [usługi BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#a-namebkmkbranchcachea-branchcache) w *sieci w programie System Center Configuration Manager i pomocy technicznej dla systemu Windows funkcji*.

-   **Skonfiguruj sposób komunikacji urządzeń klienckich z punktem dystrybucji**: Istnieją wady i zalety korzystania z protokołów HTTP i HTTPS. Aby uzyskać więcej informacji, zobacz "Najlepsze rozwiązania dotyczące zarządzania zawartością" w [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   **Zezwalaj klientom na anonimowe połączenia**: To ustawienie określa, czy punkt dystrybucji będzie zezwalał na anonimowe połączenia od klientów programu Configuration Manager do biblioteki zawartości.  

    > [!IMPORTANT]  
    >  Naprawa aplikacji Instalatora systemu Windows może zakończyć się niepowodzeniem na komputerze klienckim nie zastosowania tego ustawienia.  
    >   
    >  Podczas wdrażania aplikacji Instalatora systemu Windows na kliencie programu Configuration Manager, Configuration Manager pobierze plik do lokalnej pamięci podręcznej na kliencie. Pliki zostaną usunięte po ukończeniu instalacji.
    >  
    >  Klient programu Configuration Manager aktualizacji listy źródłowej Instalatora Windows dla zainstalowanych aplikacji Instalatora systemu Windows ze ścieżką zawartości dla biblioteki zawartości w punktach dystrybucji skojarzone. Później po uruchomieniu akcji naprawy w aplecie Dodaj lub usuń programy na kliencie programu Configuration Manager, plik MSIExec spróbuje uzyskać dostęp do ścieżki zawartości przy użyciu anonimowego użytkownika.  
    >   
    >  Można jednak zainstalować aktualizację opisaną w artykule bazy wiedzy Microsoft [2619572](http://go.microsoft.com/fwlink/?LinkId=279699) , a następnie zmodyfikuj klucz rejestru, aby zmienić to zachowanie.  
    >   
    >  Po zainstalowaniu aktualizacji na klientach plik MSIExec będzie miał dostęp do ścieżki zawartości przy użyciu konta zalogowanego użytkownika, gdy nie zostanie wybrana opcja **Zezwalaj klientom na anonimowe połączenia** ustawienie.  

-   **Tworzenie certyfikatu z podpisem własnym lub zaimportuj certyfikat klienta infrastruktury kluczy publicznych (PKI) dla punktu dystrybucji**: Certyfikat ma następujące cele:  

    -   Uwierzytelnia punkt dystrybucji do punktu zarządzania przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.  

    -   Sprawdzenie **Włącz obsługę środowiska PXE dla klientów** polu na **ustawienia środowiska PXE** strony, certyfikat zostanie wysłany do komputerów przeprowadzających rozruch w środowisku PXE, aby umożliwić im połączenie z punktem zarządzania podczas wdrażania systemu operacyjnego.  

    Jeżeli wszystkie punkty zarządzania w lokacji są skonfigurowane dla protokołu HTTP, Utwórz certyfikat z podpisem własnym. Jeżeli punkty zarządzania są skonfigurowane dla protokołu HTTPS, zaimportuj certyfikat klienta PKI.  

    Aby zaimportować certyfikat, przejdź do pliku standardu szyfrowania kluczem publicznym (PKCS #12), który ma certyfikat PKI z następującymi wymaganiami programu Configuration Manager:  

    -   Zamierzone użycie musi obejmować uwierzytelnianie klienta.  

    -   Klucz prywatny musi włączona do wyeksportowania.  

    > [!TIP]  
    >  Nie ma żadnych określonych wymagań dotyczących podmiotu certyfikatu lub alternatywnej nazwy podmiotu (SAN), a następnie można użyć tego samego certyfikatu dla wielu punktów dystrybucji.  

     Więcej informacji o wymaganiach dla certyfikatów znajduje się w temacie [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

     Przykład wdrożenia tego certyfikatu, zobacz sekcję "Wdrażanie klienta dla punktów dystrybucji certyfikatów" w [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

-   **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości**: Wybierz to ustawienie, aby włączyć punkt dystrybucji dla wstępnie przygotowanej zawartości. Po wybraniu tego ustawienia można skonfigurować sposób działania dystrybucji podczas dystrybucji zawartości. Użytkownik może zawsze wykonaj jedną z następujących czynności:

 - Wstępne przygotowanie zawartości w punkcie dystrybucji.
 - Wstępnie przygotowywać zawartość początkową pakietu, ale stosować proces normalnej dystrybucji zawartości, gdy są dostępne aktualizacje zawartości.
 - Używanie proces normalnej dystrybucji zawartości w pakiecie.  

### <a name="drive-settings"></a>Ustawienia dysku  

> [!NOTE]  
>  Te opcje są dostępne tylko w przypadku instalowania nowego punktu dystrybucji.  

Określ ustawienia dysku dla punktu dystrybucji. Można skonfigurować maksymalnie dwóch dysków dla biblioteki zawartości oraz dwóch dysków dla udziału pakietu. Menedżer konfiguracji może używać dodatkowych dysków, gdy dwa pierwsze osiągną skonfigurowaną rezerwę wolnego miejsca. **Ustawienia dysku** strony skonfigurować priorytet dysków oraz ilość wolnego miejsca na każdym z dysków.  

-   **Rezerwacja miejsca (MB) na dysku**: Wartość skonfigurowana w tym ustawieniu określa ilość wolnego miejsca na dysku przed programu Configuration Manager wybierze inny dysk, aby kontynuować proces kopiowania z tego dysku. Pliki zawartości mogą znajdować się wiele dysków.  

-   **Lokalizacje zawartości**: Określ lokalizacje zawartości dla udziału biblioteki i pakietu zawartości. Menedżer konfiguracji kopiuje zawartość do lokalizacji głównej zawartości do momentu osiągnięcia ilości wolnego miejsca na wartość określona dla **zarezerwować miejsce na dysku (MB)**. Domyślnie lokalizacje zawartości są skonfigurowane **automatyczne**. Lokalizacją główną zawartości jest ustawiona na dysk o największej ilości wolnego miejsca podczas instalacji, a lokalizacja dodatkowa zostanie przypisana do dysku, w którym jest drugim pod względem wolnego miejsca na dysku. Gdy podstawowa i pomocnicza osiągną rezerwę wolnego miejsca, programu Configuration Manager wybierze inny dostępny dysk o największej ilości wolnego miejsca, aby kontynuować proces kopiowania.  

> [!NOTE]  
>  Aby uniemożliwić instalowanie na określonym dysku programu Configuration Manager, należy utworzyć pusty plik o nazwie **no_sms_on_drive.sms** i skopiuj go do folderu głównego dysku przed zainstalowaniem punktu dystrybucji.  

### <a name="pull-distribution-point"></a>Ściągający punkt dystrybucji  
Po wybraniu **Włącz ten punkt dystrybucji do ściągania zawartości z innych punktów dystrybucji**, zmienić zachowanie jak ten komputer pobiera zawartość do punktu dystrybucji. Staje się punktem dystrybucji.  

Dla każdego punktu dystrybucji należy określić co najmniej jeden źródłowych punktów dystrybucji z których ściągający punkt dystrybucji pobiera zawartość:  

-   Wybierz **Dodaj**, a następnie wybierz co najmniej jeden dostępny punkt dystrybucji do źródłowego punktu dystrybucji.  

-   Wybierz **Usuń** usunąć wybranego punktu dystrybucji jako źródłowy punkt dystrybucji.  

-   Użyj przycisków strzałek odpowiednio dostosuj kolejność, w jakiej ściągający punkt dystrybucji kontaktów w źródłowej punktach dystrybucji podczas prób przesłania zawartości punktu dystrybucji. Punkty dystrybucji o najniższej wartości będzie kontaktować się z najpierw.  

### <a name="pxe"></a>Opcja PXE  
Określ, czy włączyć obsługę środowiska PXE w punkcie dystrybucji. Po włączeniu obsługi środowiska PXE programu Configuration Manager instaluje usługi wdrażania systemu Windows na serwerze, w razie potrzeby. Usługi wdrażania systemu Windows to usługi przeprowadzające rozruch w środowisku PXE w celu zainstalowania systemu operacyjnego. Po zakończeniu pracy Kreatora tworzenia punktu dystrybucji programu Configuration Manager zainstaluje dostawcę w ramach usług wdrażania systemu Windows używającego funkcji rozruchu środowiska PXE.  

Po wybraniu **Włącz obsługę środowiska PXE dla klientów**, skonfiguruj następujące ustawienia:  

-   **Zezwól temu punktowi dystrybucji na odpowiadanie na przychodzące żądania środowiska PXE**: Określ, czy włączyć usługi wdrażania systemu Windows, tak aby odpowiadały na żądania usługi PXE. To pole umożliwia włączać i wyłączać usługę bez usuwania funkcji PXE z punktu dystrybucji.  

-   **Włącz obsługę nieznanych komputerów**: Określ, czy włączyć obsługę komputerów, które nie zarządza program Configuration Manager.  

-   **Wymagaj hasła, kiedy komputery używają środowiska PXE**: Aby zapewnić dodatkową ochronę wdrożeń PXE, określ silne hasło.  

-   **Koligacja urządzenia użytkownika**: Określ, jak punkt dystrybucji ma skojarzyć użytkowników z komputerem docelowym w ramach wdrożeń PXE. Wybierz jedną z następujących opcji:  

    -   **Zezwalaj na koligację urządzenia użytkownika z automatycznym zatwierdzeniem**: Wybierz to ustawienie, aby automatycznie kojarzyć użytkowników z komputerem docelowym bez czekania na zatwierdzenie.  

    -   **Zezwalaj na koligację urządzenia użytkownika w oczekiwaniu na zatwierdzenie przez administratora**: Wybierz to ustawienie, aby czekać na zatwierdzenie przez użytkownika administracyjnego przed użytkowników skojarzonych z komputerem docelowym.  

    -   **Nie zezwalaj na koligację urządzenia użytkownika**: Wybierz to ustawienie, aby określić, że użytkownicy nie są skojarzone z komputerem docelowym.  

     Aby uzyskać więcej informacji o koligacji urządzenia użytkownika, zobacz [Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   **Interfejsy sieciowe**: Określ, czy punkt dystrybucji ma odpowiadać na żądania PXE ze wszystkich interfejsów sieciowych, czy tylko z konkretnych interfejsów sieciowych. Jeśli punkt dystrybucji ma odpowiadać na określonych interfejsach sieciowych, podaj adres MAC każdego interfejsu.  

-   **Określ opóźnienie reakcji serwera PXE (sekundy)**: Określ w sekundach opóźnienie oczekiwania punktu dystrybucji przed udzieleniem odpowiedzi na żądanie komputera, gdy jest używanych wiele punktów dystrybucji z włączoną funkcją PXE. Domyślnie punkt obsługi środowiska PXE programu Configuration Manager odpowiada w pierwszej kolejności na żądania sieciowe środowiska PXE.  

> [!NOTE]  
>  Protokół PXE wdrożenia systemu operacyjnego na komputerach klienckich programu Configuration Manager można uruchomić. Configuration Manager używa roli lokacji punktu dystrybucji z włączoną obsługą środowiska PXE do zainicjowania procesu wdrażania systemu operacyjnego. Punkt dystrybucji z włączoną obsługą środowiska PXE należy skonfigurować do:
>
> 1. Odpowiadanie na żądania rozruchu środowiska PXE, które klientów programu Configuration Manager w sieci.
> 2. Interakcje z infrastrukturą programu Configuration Manager, aby określić, jakie akcje wdrażania należy podjąć.  

### <a name="multicast"></a>Multiemisji  
Określ, czy włączyć obsługę multiemisji w punkcie dystrybucji. Po włączeniu obsługi multiemisji, Configuration Manager instaluje usługi wdrażania systemu Windows na serwerze, jeśli jest to wymagane.  

Sprawdzenie **Włącz multiemisję w celu jednoczesnego wysyłania danych do wielu klientów** skonfiguruj następujące ustawienia:  

-   **Konto połączenia multiemisji**: Określ konto do użycia podczas konfigurowania połączenia bazy danych programu Configuration Manager do multiemisji.  

-   **Ustawienia adresu multiemisji**: Określ adresy IP do wysyłania danych do komputerów docelowych. Domyślnie adres IP jest pobierany z serwera DHCP, na którym jest włączona funkcja dystrybucji adresów multiemisji. W zależności od środowiska sieciowego można określić zakres adresów IP od 239.0.0.0 do 239.255.255.255.  

    > [!IMPORTANT]  
    >  Należy skonfigurować adresy IP muszą być dostępne dla komputerów docelowych, które żądają obrazu systemu operacyjnego. Sprawdź, czy routery i zapory zezwalają na ruch multiemisji między komputerem docelowym a serwerem lokacji.  

-   **Zakres portów UDP dla multiemisji**: Określ porty zakres z User Datagram Protocol (UDP), które są używane do wysyłania danych do komputerów docelowych.  

    > [!IMPORTANT]  
    >  Porty UDP muszą być dostępne dla komputerów docelowych, które żądają obrazu systemu operacyjnego. Sprawdź, czy routery i zapory zezwalają na ruch multiemisji między komputerem docelowym a serwerem lokacji.  

-   **Szybkość przesyłu klientów**: Wybierz szybkość transferu, który służy do pobierania danych do komputerów docelowych.  

-   **Maksymalna liczba klientów**: Określ maksymalną liczbę komputerów docelowych, które mogą pobierać system operacyjny z tego punktu dystrybucji.  

-   **Włącz zaplanowaną multiemisję**: Określ, jak program Configuration Manager sterować uruchamianiem wdrażania systemów operacyjnych na komputerach docelowych. Skonfiguruj następujące opcje:  

    -   **Opóźnienie rozpoczęcia sesji (minuty)**: Określ liczbę minut, które programu Configuration Manager czeka przed nim odpowiada na pierwsze żądanie wdrożenia.  

    -   **Minimalna wielkość sesji (liczba klientów)**: Określ, ile żądań musi odebrać przed uruchomieniem programu Configuration Manager do wdrażania systemu operacyjnego.  

> [!NOTE]  
>  Wdrożenia z multiemisją oszczędzania przepustowości sieci przez wysyłają dane jednocześnie do wielu klientów programu Configuration Manager, zamiast wysyłać kopię danych do każdego klienta przez oddzielne połączenie. Aby uzyskać więcej informacji o używaniu multiemisji do wdrażania systemu operacyjnego, zobacz [użyć multiemisji w celu wdrożenia systemu operacyjnego Windows za pośrednictwem sieci z System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

### <a name="group-relationships"></a>Relacje grupy  

> [!NOTE]  
>  Te opcje są dostępne tylko w przypadku edycji właściwości punktu dystrybucji zainstalowane wcześniej.  

Zarządzaj grupy punktów dystrybucji, których członkiem jest ten punkt dystrybucji.  

Aby dodać ten punkt dystrybucji jako członka do istniejącej grupy punktów dystrybucji, wybierz **Dodaj**. Wybierz istniejącą grupę punktów dystrybucji na liście w **dodać do grupy punktów dystrybucji** okna dialogowego pole, a następnie wybierz **OK**.  

Aby usunąć ten punkt dystrybucji z grupy punktów dystrybucji, wybierz grupę punktów dystrybucji na liście, a następnie wybierz **usunąć**.  

### <a name="content"></a>Zawartość  

> [!NOTE]  
>  Te opcje są dostępne tylko w przypadku edycji właściwości punktu dystrybucji zainstalowane wcześniej.  

Umożliwia zarządzanie zawartością rozesłaną do punktu dystrybucji. **Pakiety wdrożeniowe** sekcji znajduje się lista pakietów rozesłanych do tego punktu dystrybucji. Można wybrać pakiet z listy i wykonać następujące czynności:  

-   **Sprawdź poprawność**: Rozpoczyna się proces weryfikowania integralności plików zawartości w pakiecie. Aby wyświetlić wyniki procesu weryfikacji zawartości, w **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie wybierz **stan zawartości** węzła.  

-   **Ponowna dystrybucja**: Kopiuje wszystkie pliki zawartości w pakiecie do punktu dystrybucji i zastępuje istniejące pliki. Ta akcja jest zazwyczaj używają do naprawienia plików zawartości w pakiecie.  

-   **Usuń**: Usuwa pliki zawartości z punktu dystrybucji pakietu.  

### <a name="content-validation"></a>Sprawdzanie poprawności zawartości  
Określ, czy opracować harmonogram weryfikowania integralności plików zawartości w punkcie dystrybucji. Po włączeniu weryfikacji zawartości zgodnie z harmonogramem, programu Configuration Manager rozpoczyna proces w zaplanowanym czasie, a cała zawartość w punkcie dystrybucji zostanie poddana weryfikacji. Można również skonfigurować priorytet weryfikacji zawartości. Domyślnie priorytet ma wartość **najniższy**.  

Aby wyświetlić wyniki procesu weryfikacji zawartości, w **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie wybierz **stan zawartości** węzła. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy).  

> [!WARNING]  
>  Harmonogram weryfikacji zawartości można określić przy użyciu czasu lokalnego dla komputera, konsoli programu Configuration Manager zawiera harmonogram w formacie UTC.  

### <a name="boundary-group"></a>Grupy granic  
Zarządzanie grupami granic, do których jest przypisany ten punkt dystrybucji. Grupy granic można skojarzyć z punktem dystrybucji. Podczas wdrażania zawartości klienty muszą znajdować się grupie granic skojarzonej z punktem dystrybucji, aby używać go jako lokalizacji źródłowej zawartości.

Dodatkowo:

- Przed wersją 1610 można sprawdzić **Zezwalaj klientom na używanie tego systemu lokacji jako rezerwowej lokalizacji źródła zawartości** pole, aby umożliwić klientom spoza granic grup wrócić i używać punktu dystrybucji jako lokalizacji źródłowej zawartości, jeśli nie są dostępne nie inne punkty dystrybucji. Aby uzyskać więcej informacji o grupach granic, zobacz [grup granic dla wersji 1511, 1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606). Preferowanych punktów dystrybucji, można znaleźć w temacie [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).

- Z wersji 1610 lub nowszej, można skonfigurować grupę granic *relacje* definiujących po i grup granic, w których klient przełączają się znaleźć zawartości. Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


### <a name="schedule"></a>Harmonogram  

> [!NOTE]  
>  Te opcje są dostępne tylko w przypadku edycji właściwości punktu dystrybucji zainstalowane wcześniej.  

> [!TIP]  
>  Ta karta jest dostępna tylko wtedy, gdy w przypadku edycji właściwości punktu dystrybucji zdalnego wobec komputera serwera lokacji.  

 Określ, czy skonfigurować harmonogram ograniczający podczas przesyłania danych programu Configuration Manager do punktu dystrybucji.  

> [!IMPORTANT]  
>  Harmonogram jest oparty na strefie czasowej witryny wysyłania, a nie punktu dystrybucji.  

Aby ograniczyć dane, wybierz okres, a następnie wybierz jedną z następujących ustawień **dostępności**:  

-   **Otwarty dla wszystkich priorytetów**: Określa, że program Configuration Manager wysyła dane do punktu dystrybucji bez żadnych ograniczeń.  

-   **Zezwalaj na Średni i wysoki priorytet**: Określa, czy programu Configuration Manager przesyłał do punktu dystrybucji jedynie dane średnim i wysokim priorytecie.  

-   **Zezwól na wysoki priorytet tylko**: Określa, że program Configuration Manager wysyła dane tylko wysokim priorytecie do punktu dystrybucji.  

-   **Zamknięte**: Określa, że program Configuration Manager nie wysyła żadnych danych do punktu dystrybucji.  

Można ograniczyć dane według priorytetu lub zamknąć połączenie na wybrany okres.  

### <a name="rate-limits"></a>Limity szybkości  

> [!NOTE]  
>  Te opcje są dostępne tylko w przypadku edycji właściwości punktu dystrybucji zainstalowane wcześniej.  

> [!TIP]  
>  Ta karta jest dostępna tylko wtedy, gdy w przypadku edycji właściwości punktu dystrybucji zdalnego wobec komputera serwera lokacji.  

Określ, czy skonfigurować limity szybkości w celu kontroli przepustowości sieci, który jest używany podczas programu Configuration Manager jest przesyłania zawartości do punktu dystrybucji. Można wybrać następujące opcje:  

-   **Bez ograniczeń przy wysyłaniu do tego miejsca docelowego**: Ta opcja określa, czy program Configuration Manager wysyła zawartość do punktu dystrybucji bez żadnych limitów szybkości.  

-   **Tryb impulsu**: Ta opcja określa rozmiar bloków danych wysyłanych do punktu dystrybucji. Można również określić opóźnienie między wysłaniem kolejnych bloków danych. Tej opcji należy użyć przy wysyłaniu danych w połączeniu sieciowym bardzo niskiej przepustowości w punkcie dystrybucji. Może na przykład ustawić ograniczenie zezwalające na przesyłanie 1 KB danych co pięć sekund, niezależnie od szybkości łącza lub jego obciążenia w danym momencie.  

-   **Ograniczone do podanych maksymalnych szybkości transferu wg godziny**: Określ to ustawienie, aby dane były wysyłane do punktu dystrybucji przy użyciu procent czasu. Tej opcji nie będzie rozpoznawał dostępnej przepustowości sieci programu Configuration Manager, ale podzieli dostępny czas przesyłania danych. Następnie dane będą wysyłane przez krótki czas, po której następuje przedziałów czasu, gdy dane nie są wysyłane. Na przykład maksymalna szybkość wynosi **50%**, Configuration Manager przesyła dane w danym okresie czasu następuje sam okres czasu, gdy żadne dane nie są wysyłane. Zarządzanie nie dotyczy rzeczywistej ilości danych lub rozmiaru bloku danych, lecz jedynie czasu przesyłania danych.  

