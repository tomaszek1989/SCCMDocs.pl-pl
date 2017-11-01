---
title: "Zarządzaj punktami dystrybucji"
titleSuffix: Configuration Manager
description: "Obsługujące zawartość (pliki i oprogramowanie), wdrażanego na urządzeniach i użytkowników przy użyciu punktów dystrybucji. Poniżej przedstawiono sposób instalowania i konfigurowania ich."
ms.custom: na
ms.date: 09/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aebafaf9-b3d5-4a0f-9ee5-685758c037a1
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b9b2fdcff572127e9e78d7e7acba89bc4c6759a2
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="install-and-configure-distribution-points-for-system-center-configuration-manager"></a>Instalowanie i konfigurowanie punktów dystrybucji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Należy zainstalować System Center Configuration Manager punkty dystrybucji obsługujące zawartość (pliki i oprogramowanie), który można wdrożyć na urządzeniach i użytkowników. Można również utworzyć dystrybucji grupy punktów, które upraszcza sposób zarządzania punktami dystrybucji i sposób dystrybucji zawartości do punktów dystrybucji.  

 Gdy użytkownik *instalowania nowego punktu dystrybucji* (przy użyciu Kreatora instalacji) lub *zarządzania właściwościami istniejącego punktu dystrybucji* (edytując właściwości punktu dystrybucji), można skonfigurować większość ustawień punktu dystrybucji. Kilka ustawienia są dostępne tylko wtedy, gdy użytkownik w przypadku instalowania lub edytowania, ale nie obu:  

-   Ustawienia, które są dostępne tylko podczas instalowania punktu dystrybucji:  

    -   **Zezwalaj na zainstalowanie usług IIS na komputerze punktu dystrybucji program Configuration Manager**

    -   **Konfiguruj ustawienia miejsca na dysku dla punktu dystrybucji**  

-   Ustawienia, które są dostępne tylko podczas edytowania właściwości punktu dystrybucji:  

    -   **Zarządzanie relacjami grupy punktów dystrybucji**  

    -   **Wyświetl zawartość wdrożoną w punkcie dystrybucji**  

    -   **Konfiguruj limity szybkości transferu danych do punktów dystrybucji**  

    -   **Konfiguruj harmonogramy transferów danych do punktów dystrybucji**  

##  <a name="bkmk_install"></a>Instalowanie punktu dystrybucji  
Należy wyznaczyć serwer systemu lokacji jako punktu dystrybucji przed zawartości mogą zostać udostępnione na komputerach klienckich. Należy również przypisać do co najmniej jednego punktu dystrybucji [grupy granic](/sccm/core/servers/deploy/configure/boundary-groups#distribution-points) przed lokalnymi komputery klienckie mogą używać tego punktu dystrybucji jako lokalizacji źródła zawartości. Możesz dodać roli lokacji punktu dystrybucji do nowego serwera systemu lokacji lub dodać rolę lokacji do istniejącego serwera systemu lokacji.


 Podczas instalowania nowego punktu dystrybucji, należy użyć Kreatora instalacji, który przeprowadzi Cię przez kolejne dostępne ustawienia. Przed rozpoczęciem należy rozważyć następujące kwestie:  

-   Musi mieć następujące uprawnienia zabezpieczeń, aby utworzyć i skonfigurować punkt dystrybucji:  

    -   **Odczyt** dla **punktu dystrybucji** obiektu  

    -   **Kopiuj do punktu dystrybucji** dla **punktu dystrybucji** obiektu  

    -   **Modyfikowanie** dla **lokacji** obiektu  

    -   **Zarządzaj certyfikatami wdrożenia systemu operacyjnego** dla **lokacji** obiektu  

-   Internet Information Services (IIS) musi być zainstalowany na serwerze, który będzie hostem punktu dystrybucji. Podczas instalowania roli systemu lokacji programu Configuration Manager można zainstalować i skonfigurować usługi IIS.  

Aby zainstalować lub zmienić punkt dystrybucji, należy użyć poniższych procedur podstawowych. Aby uzyskać szczegółowe informacje na temat dostępnych opcji konfiguracji, zobacz [konfigurowania punktu dystrybucji](#bkmk_configs) tego tematu.  

#### <a name="to-install-a-distribution-point"></a>Aby zainstalować punkt dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji** >  **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

2.  Dodaj rolę systemu lokacji punktu dystrybucji do serwera systemu lokacji do nowego lub istniejącego:  

    -   **Nowy serwer systemu lokacji**: Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz serwer systemu lokacji**. Otworzy się Kreator tworzenia serwera systemu lokacji.  

    -   **Istniejący serwer systemu lokacji**: Wybierz serwer, w którym chcesz zainstalować rolę systemu lokacji punktu dystrybucji. Po wybraniu serwera w okienku wyników zostanie wyświetlona lista ról systemu lokacji, które są już zainstalowane na serwerze.  

         Na **Home** karcie **serwera** grupy, wybierz **Dodaj rolę systemu lokacji**. Otworzy się Kreator dodawania ról systemu lokacji.  

3.  Na stronie **Ogólne** określ ustawienia ogólne serwera systemu lokacji. Po dodaniu punktu dystrybucji do istniejącego serwera systemu lokacji należy sprawdzić wcześniej skonfigurowane wartości.  

4.  Na **Wybór roli systemu** wybierz pozycję **punktu dystrybucji** z listy dostępnych ról, a następnie wybierz pozycję **dalej**.  

5.  Na kolejnych stronach kreatora, zobacz informacje w [konfigurowania punktu dystrybucji](#bkmk_configs) sekcji.  

     Na przykład, jeśli chcesz zainstalować punkt dystrybucji jako punktu dystrybucji ściągania, możesz wybrać **Włącz ten punkt dystrybucji do ściągania zawartości z innych punktów dystrybucji** , a następnie wprowadź dodatkowe konfiguracje, które wymagają ściągających punktów dystrybucji.  

6.  Po zakończeniu działania kreatora roli lokacji punktu dystrybucji jest dodawany do serwera systemu lokacji.  

#### <a name="to-change-a-distribution-point"></a>Aby zmienić punkt dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji** >  **punktów dystrybucji**, a następnie wybierz punkt dystrybucji, który chcesz skonfigurować.  

2.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

3.  Skorzystaj z informacji w [konfigurowania punktu dystrybucji](#bkmk_configs) sekcji podczas edytowania właściwości punktu dystrybucji.  

4.  Po wprowadzeniu zmian, które chcesz zapisać ustawienia i zamknij właściwości punktu dystrybucji.  

##  <a name="bkmk_manage"></a>Zarządzanie grupami punktów dystrybucji  
 Grupy punktów dystrybucji umożliwiają logiczne grupowanie punktów dystrybucji w dystrybucji zawartości. Zarządzanie i monitorowanie zawartości z centralnej lokalizacji punktów dystrybucji, obejmującej wiele lokacji można używać tych grup. Należy pamiętać, że:

-   Do grupy punktów dystrybucji, można dodać jeden lub więcej punktów dystrybucji z dowolnej lokacji w hierarchii.  

-   Punkt dystrybucji można dodać do więcej niż jednej grupy punktów dystrybucji.  

-   Podczas dystrybucji zawartości do grupy punktów dystrybucji programu Configuration Manager dystrybuuje zawartość do wszystkich punktów dystrybucji, które są elementami członkowskimi grupy punktów dystrybucji.  

-   Jeśli dodasz po początkowej dystrybucji zawartości punktu dystrybucji do grupy punktów dystrybucji programu Configuration Manager automatycznie dystrybuuje zawartość do nowego członka punktu dystrybucji.  

-   Można skojarzyć kolekcję z grupą punktów dystrybucji. Podczas dystrybucji zawartości do kolekcji programu Configuration Manager określa grupy punktów dystrybucji, które są skojarzone z tą kolekcją. Zawartość jest dystrybuowana do wszystkich punktów dystrybucji należących do tych grup punktów dystrybucji.  

    > [!NOTE]  
    >  Po dystrybucji zawartości do kolekcji, jeśli kolekcja następnie skojarzona z grupą punktów dystrybucji, należy ponownie rozesłać zawartość do kolekcji przed zawartość jest dystrybuowana do nowej grupy punktów dystrybucji.  

#### <a name="to-create-and-configure-a-new-distribution-point-group"></a>Aby utworzyć i skonfigurować nową grupę punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **grup punktów dystrybucji**.  

2.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz grupę**.  

3.  Wprowadź nazwę i opis grupy punktów dystrybucji.  

4.  Na **kolekcje** , wybierz pozycję **Dodaj**, wybierz kolekcje, które chcesz skojarzyć z grupą punktów dystrybucji, a następnie wybierz pozycję **OK**.  

5.  Na **członków** , wybierz pozycję **Dodaj**, wybierz punkty dystrybucji, które chcesz dodać jako członków grupy punktów dystrybucji, a następnie wybierz pozycję **OK**.  

6.  Wybierz **OK** Aby utworzyć grupę punktów dystrybucji.  

#### <a name="to-add-distribution-points-and-associate-collections-with-an-existing-distribution-point-group"></a>Aby dodać punkty dystrybucji i skojarzyć kolekcje z istniejącą grupę punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **grup punktów dystrybucji**.  

2.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

3.  Na **kolekcje** , wybierz pozycję **Dodaj** aby wybrać kolekcje, które chcesz skojarzyć z grupą punktów dystrybucji, a następnie wybierz pozycję **OK**.  

4.  Na **członków** , wybierz pozycję **Dodaj** aby wybrać punkty dystrybucji, które chcesz dodać jako członków grupy punktów dystrybucji, a następnie wybierz pozycję **OK**.  

5.  Wybierz **OK** można zapisać zmian w grupie punktów dystrybucji.  

#### <a name="to-add-selected-distribution-points-to-a-new-distribution-point-group"></a>Aby dodać wybrane dystrybucji punkty do nowej grupy punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **punktów dystrybucji**, a następnie wybierz punkty dystrybucji, które chcesz dodać do nowej grupy punktów dystrybucji.  

2.  Na **Home** karcie **punktu dystrybucji** grupy, rozwiń węzeł **Dodaj wybrane elementy**, a następnie wybierz pozycję **Dodaj wybrane elementy do nowej grupy punktów dystrybucji**.  

3.  Wprowadź nazwę i opis grupy punktów dystrybucji.  

4.  Na **kolekcje** , wybierz pozycję **Dodaj** aby wybrać kolekcje, które chcesz skojarzyć z grupą punktów dystrybucji, a następnie wybierz pozycję **OK**.  

5.  Na **członków** karcie, upewnij się, że program Configuration Manager, aby dodać punkty dystrybucji znajdujące się jako członków grupy punktów dystrybucji. Wybierz **Dodaj** dodać punkty dystrybucji, a następnie wybierz pozycję **OK**.  

6.  Wybierz **OK** Aby utworzyć grupę punktów dystrybucji.  

#### <a name="to-add-selected-distribution-points-to-existing-distribution-point-groups"></a>Aby dodać wybrane dystrybucji punkty do istniejących grup punktów dystrybucji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **punktów dystrybucji**, a następnie wybierz punkty dystrybucji, które chcesz dodać do nowej grupy punktów dystrybucji.  

2.  Na **Home** karcie **punktu dystrybucji** grupy, rozwiń węzeł **Dodaj wybrane elementy**, a następnie wybierz pozycję **Dodaj wybrane elementy do istniejących grup punktów dystrybucji**.  

3.  W **dostępne grupy punktów dystrybucji**, wybierz grupy punktów dystrybucji, do których wybrane punkty dystrybucji są dodawane jako elementy członkowskie, a następnie wybierz **OK**.  

##  <a name="bkmk_configs"></a>Skonfiguruj punkt dystrybucji  
 Poszczególne punkty dystrybucji obsługują szereg różnych konfiguracji. Jednak nie wszystkie typy punktów dystrybucji obsługują wszystkie konfiguracje. Na przykład punkty dystrybucji w chmurze nie obsługują wdrożeń zawartości z obsługą środowiska PXE lub multiemisji. Informacje o ograniczeniach określonych można znaleźć w następujących tematach:  

-   [Użyj punktu dystrybucji w chmurze w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md)  

-   [Użyj punktu dystrybucji ściągania w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point)  

W poniższych sekcjach opisano konfiguracje, które można wybrać podczas instalowania nowego punktu dystrybucji lub edytowania właściwości istniejącego punktu dystrybucji.  

### <a name="general"></a>Ogólne  
 Skonfiguruj ogólne ustawienia punktu dystrybucji:  

-   **Instalowanie i konfigurowanie usług IIS, jeśli jest to wymagane przez program Configuration Manager**: Wybierz to ustawienie, aby umożliwić programowi Configuration Manager zainstalowanie i skonfigurowanie usług IIS na serwerze, jeśli nie jest już zainstalowany. Usługi IIS muszą być zainstalowane we wszystkich punktach dystrybucji. Jeśli na serwerze nie zainstalowano usług IIS i to ustawienie nie zostanie wybrane, należy zainstalować usług IIS, aby można było pomyślnie zainstalować punkt dystrybucji.  

    > [!NOTE]  
    >  Ta opcja jest dostępna tylko w przypadku instalowania nowego punktu dystrybucji.  

- **Włącz i skonfiguruj usługę BranchCache dla tego punktu dystrybucji**: Wybierz to ustawienie, aby umożliwić programowi Configuration Manager, skonfiguruj usługi Windows BranchCache na serwerze punktu dystrybucji. Aby uzyskać więcej informacji o programie System Center Configuration Manager za pomocą usługi Windows BranchCache, zobacz [usługi BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#a-namebkmkbranchcachea-branchcache) w *funkcji pomocy technicznej dla systemu Windows i sieci w programie System Center Configuration Manager*.

-   **Skonfiguruj sposób komunikacji urządzeń klienckich z punktem dystrybucji**: Brak zalety i wady przy użyciu protokołu HTTP i HTTPS. Aby uzyskać więcej informacji, zobacz "Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zarządzania zawartością" w [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   **Zezwalaj klientom na anonimowe połączenia**: To ustawienie określa, czy punkt dystrybucji będzie zezwalał na anonimowe połączenia od klientów programu Configuration Manager do biblioteki zawartości.  

    > [!IMPORTANT]  
    >  Naprawa aplikacji Instalatora systemu Windows może zakończyć się niepowodzeniem na komputerze klienckim, gdy to ustawienie nie jest używana.  
    >   
    >  Podczas wdrażania aplikacji Instalatora Windows na kliencie programu Configuration Manager, Configuration Manager pobierze plik do lokalnej pamięci podręcznej na kliencie. Pliki zostaną usunięte po zakończeniu instalacji.
    >  
    >  Klient programu Configuration Manager aktualizacji listy źródłowej Instalatora Windows dla zainstalowanych aplikacji Instalatora systemu Windows ze ścieżką do biblioteki zawartości w skojarzonych punktach dystrybucji. Później po uruchomieniu akcji naprawy z apletu Dodaj lub usuń programy na komputerze klienckim programu Configuration Manager, plik MSIExec spróbuje uzyskać dostęp do ścieżki zawartości przy użyciu anonimowego użytkownika.  
    >   
    >  Można jednak zainstalować aktualizację opisaną w artykule bazy wiedzy Microsoft Knowledge Base [2619572](http://go.microsoft.com/fwlink/?LinkId=279699) , a następnie zmodyfikować klucz rejestru, aby zmienić to zachowanie.  
    >   
    >  Po zainstalowaniu aktualizacji na klientach plik MSIExec będą uzyskiwać dostęp do ścieżki zawartości przy użyciu konta zalogowanego użytkownika, jeśli nie wybierzesz **Zezwalaj klientom na anonimowe połączenia** ustawienie.  

-   **Utwórz certyfikat z podpisem własnym lub zaimportuj certyfikat klienta infrastruktury kluczy publicznych (PKI) dla punktu dystrybucji**: Certyfikat ma następujące cele:  

    -   Uwierzytelnia punkt dystrybucji do punktu zarządzania przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.  

    -   Sprawdzenie **Włącz obsługę środowiska PXE dla klientów** polu na **ustawienia środowiska PXE** strony, certyfikat zostanie wysłany do komputerów przeprowadzających rozruch w środowisku PXE, aby umożliwić im połączenie z punktem zarządzania podczas wdrażania systemu operacyjnego.  

    Jeżeli wszystkie punkty zarządzania w lokacji są skonfigurowane do obsługi protokołu HTTP, należy utworzyć certyfikat z podpisem własnym. Jeżeli punkty zarządzania są skonfigurowane dla protokołu HTTPS, zaimportuj certyfikat klienta infrastruktury kluczy publicznych.  

    Aby zaimportować certyfikat, przejdź do pliku publicznego klucza Cryptography Standard (PKCS #12), który ma certyfikat PKI z następującymi wymaganiami programu Configuration Manager:  

    -   Zamierzone użycie musi obejmować uwierzytelnianie klienta.  

    -   Klucz prywatny musi być włączony do wyeksportowania.  

    > [!TIP]  
    >  Nie istnieją określone wymagania dla podmiotu certyfikatu lub alternatywnej nazwy podmiotu (SAN), a następnie można użyć tego samego certyfikatu dla wielu punktów dystrybucji.  

     Więcej informacji o wymaganiach dla certyfikatów znajduje się w temacie [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

     Przykład wdrożenia tego certyfikatu, zobacz sekcję "Wdrażanie klienta certyfikatu dla punktów dystrybucji" w [krok Przykładowe wdrożenie infrastruktury kluczy publicznych certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates).  

-   **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości**: Wybierz to ustawienie, aby włączyć punkt dystrybucji dla wstępnie przygotowanej zawartości. Po wybraniu tego ustawienia można skonfigurować sposób działania dystrybucji podczas dystrybucji zawartości. Użytkownik może zawsze wykonaj jedną z następujących czynności:

 - Wstępne przygotowanie zawartości w punkcie dystrybucji.
 - Wstępne przygotowanie początkowej zawartości pakietu, ale użyj normalny proces dystrybucji, gdy są dostępne aktualizacje zawartości.
 - Stosować normalny proces dystrybucji zawartości w pakiecie.  

### <a name="drive-settings"></a>Ustawienia dysku  

> [!NOTE]  
>  Te opcje są dostępne tylko w przypadku instalowania nowego punktu dystrybucji.  

Określ ustawienia dysku dla punktu dystrybucji. Można skonfigurować maksymalnie dwóch dysków dla biblioteki zawartości oraz dwóch dysków dla udziału pakietu. Menedżer konfiguracji może używać dodatkowych dysków, gdy dwa pierwsze osiągną skonfigurowaną rezerwę wolnego miejsca. **Ustawienia dysku** strony skonfigurować priorytet dysków oraz ilość wolnego miejsca, które pozostają na każdym z dysków.  

-   **Rezerwacja miejsca (MB) na dysku**: Wartość skonfigurowana w tym ustawieniu określa ilość wolnego miejsca na dysku przed programu Configuration Manager wybierze inny dysk, aby kontynuować proces kopiowania do tego dysku. Pliki zawartości mogą znajdować się na wielu dyskach.  

-   **Lokalizacje zawartości**: Określ lokalizacje zawartości dla zawartości biblioteki i udziału pakietu. Menedżer konfiguracji kopiuje zawartość do lokalizacji głównej zawartości do momentu osiągnięcia ilości wolnego miejsca ustawieniu wartość określona dla **Rezerwacja miejsca na dysku (MB)**. Domyślnie lokalizacje zawartości są skonfigurowane **automatyczne**. Lokalizacją główną zawartości jest ustawiona na dysk o największej ilości wolnego miejsca podczas instalacji, a lokalizacja dodatkowa zostanie przypisana do dysku, w którym jest najbardziej sekundę wolnego miejsca na dysku. Gdy podstawowych i pomocniczych osiągną rezerwę wolnego miejsca, programu Configuration Manager wybierze inny dostępny dysk o największej ilości wolnego miejsca, aby kontynuować proces kopiowania.  

> [!NOTE]  
>  Aby zapobiec instalacji na określonym dysku programu Configuration Manager, Utwórz pusty plik o nazwie **no_sms_on_drive.sms** i skopiować go do folderu głównego dysku przed zainstalowaniem punktu dystrybucji.  

### <a name="pull-distribution-point"></a>Ściągający punkt dystrybucji  
Po wybraniu **Włącz ten punkt dystrybucji do ściągania zawartości z innych punktów dystrybucji**, zmiany zachowania jak komputera pobiera zawartości dystrybuowanej do punktu dystrybucji. Staje się on punktem dystrybucji ściągania.  

Dla każdego punktu dystrybucji ściągania, które można skonfigurować należy określić co najmniej jeden źródłowe punkty dystrybucji spośród których ściągający punkt dystrybucji pobiera zawartość:  

-   Wybierz **Dodaj**, a następnie wybierz co najmniej jeden dostępny punkt dystrybucji jako źródłowy punkt dystrybucji.  

-   Wybierz **Usuń** można usunąć wybranego punktu dystrybucji jako źródłowy punkt dystrybucji.  

-   Użyj przycisków strzałek, aby dostosować kolejność, w jakiej ściągający punkt dystrybucji kontaktów punkty dystrybucji źródła, gdy punkt dystrybucji ściągania podejmie próbę transferu zawartości. Punkty dystrybucji o najniższej wartości są najpierw kontakt.  

### <a name="pxe"></a>Opcja PXE  
Określ, czy włączyć obsługę środowiska PXE w punkcie dystrybucji. Po włączeniu obsługi środowiska PXE programu Configuration Manager instaluje usługi wdrażania systemu Windows na serwerze, jeśli jest to wymagane. Usługi wdrażania systemu Windows to usługa, która wykonuje rozruch w środowisku PXE w celu instalacji systemów operacyjnych. Po ukończeniu czynności kreatora tworzenia punktu dystrybucji programu Configuration Manager zainstaluje dostawcę w ramach usług wdrażania systemu Windows używającego funkcji rozruchu środowiska PXE.  

Po wybraniu **Włącz obsługę środowiska PXE dla klientów**, skonfiguruj następujące ustawienia:  

-   **Zezwól temu punktowi dystrybucji na odpowiadanie na przychodzące żądania środowiska PXE**: Określ, czy włączyć usługi wdrażania systemu Windows, tak aby odpowiadały na żądania usługi PXE. Użyj tego pola, aby włączać i wyłączać usługę bez usuwania funkcji PXE z punktu dystrybucji.  

-   **Włącz obsługę nieznanych komputerów**: Określ, czy włączyć obsługę komputerów, które nie zarządza programu Configuration Manager.  

-   **Wymagaj hasła, kiedy komputery używają środowiska PXE**: Aby zapewnić dodatkową ochronę wdrożeń PXE, należy określić silne hasło.  

-   **Koligacja urządzenia użytkownika**: Określ, jak punkt dystrybucji ma skojarzyć użytkowników z komputerem docelowym w ramach wdrożeń PXE. Wybierz jedną z następujących opcji:  

    -   **Zezwalaj na koligację urządzenia użytkownika z automatycznym zatwierdzeniem**: Wybierz to ustawienie, aby automatycznie kojarzyć użytkowników z komputerem docelowym bez czekania na zatwierdzenie.  

    -   **Zezwalaj na koligację urządzenia użytkownika w oczekiwaniu na zatwierdzenie przez administratora**: Wybierz to ustawienie, aby czekać na zatwierdzenie przez użytkownika administracyjnego przed użytkowników skojarzonych z komputerem docelowym.  

    -   **Nie zezwalaj na koligację urządzenia użytkownika**: Wybierz to ustawienie, aby określić, że użytkownicy nie są skojarzone z komputerem docelowym.  

     Aby uzyskać więcej informacji o koligacji urządzenia użytkownika, zobacz [Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   **Interfejsy sieciowe**: Określ, czy punkt dystrybucji ma odpowiadać na żądania PXE ze wszystkich interfejsów sieciowych, czy tylko z konkretnych interfejsów sieciowych. Jeśli punkt dystrybucji ma odpowiadać na określonych interfejsach sieciowych, podaj adres MAC każdego interfejsu sieciowego.  

-   **Określ opóźnienie reakcji serwera PXE (sekundy)**: Określ w sekundach opóźnienie oczekiwania punktu dystrybucji przed udzieleniem odpowiedzi na żądanie komputera, gdy jest używanych wiele punktów dystrybucji z włączoną funkcją PXE. Domyślnie punkt obsługi środowiska PXE programu Configuration Manager odpowiada w pierwszej kolejności na żądania sieciowe środowiska PXE.  

> [!NOTE]  
>  Można użyć protokołu PXE można uruchomić wdrożeń systemu operacyjnego na komputerach klienckich programu Configuration Manager. Configuration Manager używa roli lokacji punktu dystrybucji z włączoną obsługą środowiska PXE do zainicjowania procesu wdrażania systemu operacyjnego. Punkt dystrybucji z włączoną obsługą środowiska PXE należy skonfigurować w taki sposób, aby:
>
> 1. Odpowiadanie na żądania rozruchu środowiska PXE, które klientów programu Configuration Manager w sieci.
> 2. Interakcje z infrastrukturą programu Configuration Manager, aby określić, jakie akcje wdrażania należy podjąć.  

### <a name="multicast"></a>Multiemisji  
Określ, czy włączyć obsługę multiemisji w punkcie dystrybucji. Po włączeniu obsługi multiemisji, Configuration Manager instaluje usługi wdrażania systemu Windows na serwerze, jeśli jest to wymagane.  

Sprawdzenie **Włącz multiemisję w celu jednoczesnego wysyłania danych do wielu klientów** skonfiguruj następujące ustawienia:  

-   **Konto połączenia multiemisji**: Określ konto do użycia podczas konfigurowania połączenia z bazą danych programu Configuration Manager do multiemisji.  

-   **Ustawienia adresu multiemisji**: Określ adresy IP do wysyłania danych do komputerów docelowych. Domyślnie adres IP jest pobierany z serwera DHCP, na którym jest włączona funkcja dystrybucji adresów multiemisji. W zależności od środowiska sieciowego można określić zakres adresów IP od 239.0.0.0 do 239.255.255.255.  

    > [!IMPORTANT]  
    >  Należy skonfigurować adresy IP muszą być dostępne dla komputerów docelowych, które żądają obrazu systemu operacyjnego. Sprawdź, czy routery i zapory zezwalają na ruch multiemisji między komputerem docelowym a serwerem lokacji.  

-   **Zakres portów UDP dla multiemisji**: Określ porty zakresu z User Datagram Protocol (UDP), które są używane do wysyłania danych do komputerów docelowych.  

    > [!IMPORTANT]  
    >  Porty UDP muszą być dostępne dla komputerów docelowych, które żądają obrazu systemu operacyjnego. Sprawdź, czy routery i zapory zezwalają na ruch multiemisji między komputerem docelowym a serwerem lokacji.  

-   **Szybkość przesyłu klientów**: Wybierz szybkość transferu, który służy do pobierania danych do komputerów docelowych.  

-   **Maksymalna liczba klientów**: Określ maksymalną liczbę komputerów docelowych, które mogą pobierać system operacyjny z tego punktu dystrybucji.  

-   **Włącz zaplanowaną multiemisję**: Określ, jak programu Configuration Manager sterować uruchamianiem wdrażania systemów operacyjnych na komputerach docelowych. Skonfiguruj następujące opcje:  

    -   **Opóźnienie rozpoczęcia sesji (minuty)**: Określ liczbę minut, przez które programu Configuration Manager czeka przed nią odpowiada na pierwsze żądanie wdrożenia.  

    -   **Minimalna wielkość sesji (liczba klientów)**: Określ, ile żądań musi odebrać przed uruchomieniem programu Configuration Manager do wdrażania systemu operacyjnego.  

> [!NOTE]  
>  Wdrożenia multiemisyjne oszczędzenia przepustowości sieci przez wysyłają dane jednocześnie do wielu klientów programu Configuration Manager, zamiast wysyłać kopię danych do każdego klienta przez oddzielne połączenie. Aby uzyskać więcej informacji o używaniu multiemisji do wdrażania systemu operacyjnego, zobacz [użyć multiemisji do wdrażania systemu Windows za pośrednictwem sieci w programie System Center Configuration Manager](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network.md).  

### <a name="group-relationships"></a>Relacje grupy  

> [!NOTE]  
>  Te opcje są dostępne tylko podczas edytowania właściwości uprzednio zainstalowanego punktu dystrybucji.  

Zarządzanie grupami punktów dystrybucji, których członkiem jest ten punkt dystrybucji.  

Aby dodać ten punkt dystrybucji jako członka do istniejącej grupy punktów dystrybucji, wybierz **Dodaj**. Wybierz istniejącą grupę punktów dystrybucji na liście w **dodać do grupy punktów dystrybucji** okna dialogowego polu, a następnie wybierz pozycję **OK**.  

Aby usunąć ten punkt dystrybucji z grupy punktów dystrybucji, wybierz grupę punktów dystrybucji na liście, a następnie wybierz pozycję **Usuń**.  

### <a name="content"></a>Zawartość  

> [!NOTE]  
>  Te opcje są dostępne tylko podczas edytowania właściwości uprzednio zainstalowanego punktu dystrybucji.  

Zarządzanie zawartości dystrybuowanej do punktu dystrybucji. **Pakiety wdrożeniowe** sekcja zawiera listę pakietów do tego punktu dystrybucji. Możesz wybrać pakiet z listy i wykonaj następujące czynności:  

-   **Sprawdź poprawność**: Uruchamia procesy weryfikacji integralność plików zawartości w pakiecie. Aby wyświetlić wyniki procesu weryfikacji zawartości w **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie wybierz pozycję **stan zawartości** węzła.  

-   **Ponowna dystrybucja**: Kopiuje wszystkie pliki zawartości w pakiecie do punktu dystrybucji i zastępuje istniejące pliki. Ta akcja jest zazwyczaj służy do naprawienia plików zawartości w pakiecie.  

-   **Usuń**: Usuwa pliki zawartości z punktu dystrybucji dla pakietu.  

### <a name="content-validation"></a>Sprawdzanie poprawności zawartości  
Określ, czy skonfigurować harmonogram, aby zweryfikować integralność plików zawartości w punkcie dystrybucji. Po włączeniu weryfikacji zawartości zgodnie z harmonogramem, programu Configuration Manager rozpoczyna proces w zaplanowanym czasie, a cała zawartość w punkcie dystrybucji zostanie poddana weryfikacji. Można również skonfigurować priorytet weryfikacji zawartości. Domyślnie priorytet ma ustawioną **najniższy**.  

Aby wyświetlić wyniki procesu weryfikacji zawartości w **monitorowanie** obszaru roboczego, rozwiń węzeł **stan dystrybucji**, a następnie wybierz pozycję **stan zawartości** węzła. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy).  

> [!WARNING]  
>  Mimo że można określić harmonogramu weryfikacji zawartości przy użyciu czasu lokalnego na komputerze, konsola programu Configuration Manager zawiera harmonogram w formacie UTC.  

### <a name="boundary-group"></a>Grupy granic  
Zarządzanie grupami granic, do których jest przypisany ten punkt dystrybucji. Planowanie dodać punkt dystrybucji do co najmniej jednej grupy granic. Podczas wdrażania zawartości klienci muszą być w grupie granic skojarzonej z punktem dystrybucji na użycie tego punktu dystrybucji jako lokalizacji źródłowej zawartości.

Dodatkowo:

- Przed wersją 1610, można sprawdzić **Zezwalaj klientom na używanie tego systemu lokacji jako rezerwowej lokalizacji źródła zawartości** pole, aby umożliwić klientom spoza grup granic na rezerwowe używanie punktu dystrybucji jako lokalizacji źródłowej zawartości, jeśli preferowane punkty dystrybucji nie są dostępne. Aby uzyskać więcej informacji o grupach granic, zobacz [grup granic dla wersji 1511, 1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606). Do preferowanych punktów dystrybucji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).

- Z wersji 1610 lub nowszej, skonfiguruj grupy granic *relacje* definiującą po i do grupy granic, które klient może przełączyć się na znajdowanie zawartości. Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


### <a name="schedule"></a>Harmonogram  

> [!NOTE]  
>  Te opcje są dostępne tylko podczas edytowania właściwości uprzednio zainstalowanego punktu dystrybucji.  

> [!TIP]  
>  Ta karta jest dostępna tylko podczas edytowania właściwości punktu dystrybucji, sterowanym zdalnie z komputera serwera lokacji.  

 Określ, czy skonfigurować harmonogram ograniczający podczas przesyłania danych programu Configuration Manager do punktu dystrybucji.  

> [!IMPORTANT]  
>  Harmonogram jest oparty na strefie czasowej witryny wysyłania, a nie punktu dystrybucji.  

Aby ograniczyć dane, wybierz okres, a następnie wybierz jedną z następujących ustawień **dostępności**:  

-   **Otwarty dla wszystkich priorytetów**: Określa, że programu Configuration Manager wysyła dane do punktu dystrybucji bez żadnych ograniczeń.  

-   **Zezwalaj na Średni i wysoki priorytet**: Określa, że programu Configuration Manager przesyłał do punktu dystrybucji jedynie dane średnim i wysokim priorytecie.  

-   **Zezwalaj tylko na wysoki priorytet**: Określa, że programu Configuration Manager wysyła dane tylko o wysokim priorytecie, punkt dystrybucji.  

-   **Zamknięte**: Określa, że Menedżer konfiguracji nie wysyła żadnych danych do punktu dystrybucji.  

Można ograniczyć dane według priorytetu lub zamknąć połączenie na wybrany okres.  

### <a name="rate-limits"></a>Limity szybkości  

> [!NOTE]  
>  Te opcje są dostępne tylko podczas edytowania właściwości uprzednio zainstalowanego punktu dystrybucji.  

> [!TIP]  
>  Ta karta jest dostępna tylko podczas edytowania właściwości punktu dystrybucji, sterowanym zdalnie z komputera serwera lokacji.  

Określ, czy skonfigurować limity szybkości do kontroli przepustowości sieci, który jest używany w przypadku programu Configuration Manager jest przesyłania zawartości do punktu dystrybucji. Można wybrać następujące opcje:  

-   **Bez ograniczeń przy wysyłaniu do tego miejsca docelowego**: Ta opcja określa, że Menedżera konfiguracji wysyła zawartość do punktu dystrybucji bez żadnych limitów szybkości.  

-   **Tryb impulsu**: Ta opcja określa rozmiar bloków danych wysyłanych do punktu dystrybucji. Można również określić opóźnienie między wysłaniem kolejnych bloków danych. Użyj tej opcji, po wysłaniu danych przez połączenie sieciowe o bardzo niskiej przepustowości do punktu dystrybucji. Może na przykład ustawić ograniczenie zezwalające na przesyłanie 1 KB danych co pięć sekund, niezależnie od szybkości łącza lub jego obciążenia w danym momencie.  

-   **Ograniczone do podanych maksymalnych szybkości transferu wg godziny**: Określ to ustawienie, aby dane były wysyłane do punktu dystrybucji przy użyciu tylko procent czasu, które można skonfigurować. Tej opcji programu Configuration Manager nie będzie rozpoznawał dostępnej przepustowości sieci, ale podzieli dostępny czas przesyłania danych. Następnie dane są wysyłane przez krótki czas, po której następuje przedziałów czasu, gdy dane nie są wysyłane. Na przykład maksymalna szybkość wynosi **50%**, programu Configuration Manager nieprzesyłania danych przez sam okres czasu, gdy żadne dane nie są wysyłane. Zarządzanie nie dotyczy rzeczywistej ilości danych lub rozmiaru bloku danych, lecz jedynie czasu przesyłania danych.  
