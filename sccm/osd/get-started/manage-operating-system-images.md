---
title: "Zarządzanie obrazami systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "W programie Configuration Manager informacje na temat metod, które umożliwiają zarządzanie obrazami systemu operacyjnego, które są przechowywane w plikach obrazów systemu Windows (WIM)."
ms.custom: na
ms.date: 12/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fab13949-371c-4a4c-978e-471db1e54966
caps.latest.revision: "17"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 6953c3834ca303b949f22436010a87b3da9688dc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-operating-system-images-with-system-center-configuration-manager"></a>Zarządzanie obrazami systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Obrazy systemu operacyjnego w programie Configuration Manager to pliki w formacie WIM (Windows Imaging) stanowiące skompresowaną kolekcję plików i folderów odniesienia wymaganych do pomyślnej instalacji i konfiguracji systemu operacyjnego na komputerze. W przypadku wszystkich scenariuszy wdrożenia systemu operacyjnego musisz wybrać obraz systemu operacyjnego.   Możesz użyć domyślnego obrazu systemu operacyjnego lub utworzyć obraz systemu operacyjnego na podstawie skonfigurowanego komputera odniesienia. Podczas tworzenia komputera odniesienia możesz dodać pliki systemu operacyjnego, sterowniki, pliki obsługi, aktualizacje oprogramowania, narzędzia i inne aplikacje do systemu operacyjnego przed przechwyceniem go w celu utworzenia pliku obrazu. Poniżej znajdują się informacje dotyczące każdej z metod.  

 **Domyślny obraz**  

 Domyślny obraz systemu operacyjnego (install.wim) jest dołączony do plików instalacji systemu operacyjnego Windows. Ten obraz to obraz podstawowego systemu operacyjnego, który zawiera standardowy zestaw sterowników. Jeśli korzystasz z domyślnego obrazu systemu operacyjnego, możesz zainstalować aplikacje i wprowadzić inne zmiany konfiguracji po zainstalowaniu systemu operacyjnego przy użyciu kroków sekwencji zadań.  Domyślny obraz systemu operacyjnego znajduje się w ścieżce <*ścieżka źródłowa systemu operacyjnego*>\Sources\install.wim.  

-   **Zalety**  

    -   Rozmiar obrazu jest mniejszy niż w przypadku przechwyconego obrazu.  

    -   Instalowanie aplikacji i przeprowadzanie konfiguracji za pomocą kroków sekwencji zadań jest bardziej dynamiczne. Na przykład możesz zmienić instalowane aplikacje i konfiguracje w sekwencji zadań bez konieczności ponownego tworzenia obrazu systemu operacyjnego.  

-   **Wady**  

    -   Instalacja systemu operacyjnego może trwać dłużej, ponieważ instalacja aplikacji i działania konfiguracji są wykonywane po zakończeniu instalacji systemu operacyjnego.  

 **Przechwycony obraz**  

 Aby utworzyć dostosowany obraz systemu operacyjnego, należy utworzyć komputer odniesienia z odpowiednim systemem operacyjnym, zainstalować aplikacje, skonfigurować ustawienia itp. Następnie należy przechwycić obraz systemu operacyjnego w celu utworzenia pliku WIM. Komputer odniesienia można skompilować ręcznie lub używając sekwencji zadań do automatyzacji niektórych lub wszystkich kroków kompilacji.   
Aby uzyskać instrukcje dotyczące tworzenia dostosowanego obrazu systemu operacyjnego, zobacz [dostosowanie obrazów systemu operacyjnego](customize-operating-system-images.md).  

-   **Zalety**  

    -   Instalacja może być szybsza niż przy użyciu domyślnego obrazu. Na przykład aplikacje mogą być zainstalowane wstępnie w przechwyconym obrazie systemu operacyjnego i nie będzie trzeba instalować ich później za pomocą kroków sekwencji zadań.  

-   **Wady**  

    -   Instalacja systemu operacyjnego może trwać dłużej, ponieważ instalacja aplikacji i działania konfiguracji są wykonywane po zakończeniu instalacji systemu operacyjnego.  


##  <a name="BKMK_AddOSImages"></a>Dodawanie obrazów systemu operacyjnego do programu Configuration Manager  
 Przed użyciem obrazu systemu operacyjnego, należy dodać obraz do lokacji programu Configuration Manager. Użyj następującej procedury, aby dodać obraz systemu operacyjnego do lokacji.  

#### <a name="to-add-an-operating-system-image-to-a-site"></a>Dodawanie obrazu systemu operacyjnego do lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Obrazy systemu operacyjnego**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj obraz systemu operacyjnego**, aby uruchomić Kreatora dodawania obrazu systemu operacyjnego.  

4.  Na stronie **Źródło danych** określ ścieżkę sieciową do obrazu systemu operacyjnego. Na przykład określ ścieżkę **\\\server\path\OS.WIM**.  

5.  Na stronie **Ogólne** określ poniższe informacje, a następnie kliknij przycisk **Dalej**. Te informacje przydają się do identyfikacji podczas dodawania wielu obrazów systemu operacyjnego do tej samej lokacji.  

    -   **Nazwa**: Określ nazwę obrazu. Domyślnie nazwa obrazu jest pobierana z pliku WIM.  

    -   **Wersja**: Określ wersję obrazu.  

    -   **Komentarz**: Podaj krótki opis obrazu.  

6.  Ukończ pracę kreatora.  

 Teraz możesz dystrybuować obraz systemu operacyjnego do punktów dystrybucji.  

##  <a name="BKMK_DistributeBootImages"></a>Dystrybuowanie obrazów systemu operacyjnego do punktów dystrybucji  
 Dystrybuowanie obrazów systemu operacyjnego do punktów dystrybucji przebiega tak samo jak w przypadku zawartości innego typu. W większości przypadków przed wdrożeniem systemu operacyjnego musisz przeprowadzić dystrybucję obrazu systemu operacyjnego do co najmniej jednego punktu dystrybucji. Aby zapoznać się z procedurą dystrybucji obrazu systemu operacyjnego, zobacz temat [Dystrybucja zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_OSImagesApplyUpdates"></a>Stosowanie aktualizacji oprogramowania do obrazu systemu operacyjnego  
 Okresowo są wydawane nowe aktualizacje oprogramowania, które mają zastosowanie do systemu operacyjnego znajdującego się w używanym obrazie. Przed zainstalowaniem aktualizacji oprogramowania do obrazu musi mieć aktualizacje oprogramowania infrastruktury w Umieść, zostały pomyślnie zsynchronizować aktualizacje oprogramowania i pobrane aktualizacje oprogramowania do biblioteki zawartości na serwerze lokacji. Aby uzyskać więcej informacji, zobacz [wdrażania aktualizacji oprogramowania](../../sum/deploy-use/deploy-software-updates.md).  

 Odpowiednie aktualizacje oprogramowania można stosować do obrazu zgodnie z zaplanowanym harmonogramem. Zgodnie z harmonogramem określonym przez użytkownika stosuje wybrane aktualizacje oprogramowania do obrazu systemu operacyjnego programu Configuration Manager, a następnie opcjonalnie dystrybuuje zaktualizowane obrazy do punktów dystrybucji. Informacje o obrazie systemu operacyjnego, w tym informacje o aktualizacjach oprogramowania zastosowanych podczas importu, są przechowywane w bazie danych lokacji. W bazie danych lokacji są także przechowywane informacje o aktualizacjach oprogramowania zastosowanych do obrazu od jego pierwszego dodania. Po uruchomieniu kreatora w celu zastosowania aktualizacji oprogramowania do obrazu systemu operacyjnego kreator pobiera listę dostępnych do wyboru aktualizacji, które nie zostały jeszcze zastosowane do obrazu. Configuration Manager kopiuje aktualizacje oprogramowania z biblioteki zawartości na serwerze lokacji i stosuje aktualizacje oprogramowania do obrazu systemu operacyjnego.  

 Aby zastosować aktualizację oprogramowania do obrazu systemu operacyjnego, należy wykonać poniższą procedurę.  

#### <a name="to-apply-software-updates-to-an-operating-system-image"></a>Aby zastosować aktualizacje oprogramowania do obrazu systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Obrazy systemu operacyjnego**.  

3.  Wybierz obraz systemu operacyjnego, do którego mają zostać zastosowane aktualizacje oprogramowania.  

4.  Na karcie **Narzędzia główne** w grupie **Obraz systemu operacyjnego** kliknij polecenie **Zaplanuj aktualizacje**, aby uruchomić kreatora.  

5.  Na stronie **Wybierz aktualizacje** wybierz aktualizacje oprogramowania, które mają zostać zastosowane do obrazu systemu operacyjnego, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Ustawianie harmonogramu** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    1.  **Harmonogram**: Określ harmonogram stosowania aktualizacji oprogramowania do obrazu systemu operacyjnego.  

    2.  **Kontynuuj przy błędzie**:  Wybierz tę opcję, aby kontynuować stosowanie aktualizacji oprogramowania do obrazu nawet wtedy, gdy występuje błąd.  

    3.  **Dokonaj dystrybucji obrazu do punktów dystrybucji**: Wybierz tę opcję, aby zaktualizować obraz systemu operacyjnego w punktach dystrybucji po zastosowaniu aktualizacji oprogramowania.  

7.  Na stronie **Podsumowanie** sprawdź informacje, a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Ukończenie** sprawdź, czy aktualizacje oprogramowania zostały pomyślnie zastosowane do obrazu systemu operacyjnego.  

##  <a name="BKMK_OSImageMulticast"></a>Przygotowywanie obrazu systemu operacyjnego dla wdrożeń multiemisji  
 Wdrożenia za pomocą multiemisji umożliwiają wielu komputerom równoczesne pobranie obrazu systemu operacyjnego. Obraz jest przekazywany za pomocą multiemisji do klientów przez punkt dystrybucji — w odróżnieniu od sytuacji, w której punkt dystrybucji wysyła kopię obrazu do każdego klienta przez oddzielne połączenie. Po wybraniu [użyć multiemisji do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-multicast-to-deploy-windows-over-the-network.md) metodę wdrożenia systemu operacyjnego, należy skonfigurować pakiet obrazu systemu operacyjnego w celu obsługi multiemisji przed rozpoczęciem dystrybucji obrazu systemu operacyjnego do punktu dystrybucji obsługującego multiemisję. Aby ustawić opcje multiemisji dla istniejącego pakietu obrazu systemu operacyjnego, należy wykonać poniższą procedurę.  

#### <a name="to-modify-an-operating-system-image-package-to-use-multicast"></a>Aby zmodyfikować pakiet obrazu systemu operacyjnego w celu użycia multiemisji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Obrazy systemu operacyjnego**.  

3.  Wybierz obraz systemu operacyjnego, który chcesz dystrybuować do punktu dystrybucji z obsługą multiemisji.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

5.  Wybierz kartę **Ustawienia dystrybucji** i ustaw poniższe opcje:  

    -   **Zezwalaj na przesłanie przy użyciu multiemisji (tylko WinPE) tego pakietu**: Musisz wybrać tę opcję dla programu Configuration Manager, aby równocześnie wdrożyć obrazy systemu operacyjnego.  

    -   **Szyfruj pakiety multiemisji**: Określ, czy obraz ma być zaszyfrowany przed wysłaniem do punktu dystrybucji. Użyj tej opcji, jeśli pakiet zawiera poufne informacje. Jeśli obraz nie jest zaszyfrowany, zawartość pakietu będzie widoczna jawny tekst w sieci i będzie możliwe jej odczytanie przez nieautoryzowanego użytkownika.  

    -   **Prześlij ten pakiet tylko przy użyciu multiemisji**: Określ, czy punkt dystrybucji w celu wdrożenia obrazu tylko podczas sesji multiemisji.  

         W przypadku wybrania opcji **Prześlij ten pakiet tylko przy użyciu multiemisji** należy także określić opcję **W razie potrzeby pobierz zawartość lokalnie przez uruchomienie sekwencji zadań** jako opcję wdrażania obrazu systemu operacyjnego. Opcje wdrażania obrazu można określić podczas wdrażania obrazu systemu operacyjnego lub w późniejszym momencie poprzez edycję właściwości wdrożenia. Opcje wdrażania są dostępne na karcie **Punkty dystrybucji** na stronie **Właściwości** obiektu wdrożenia.  

6.  Kliknij przycisk **OK**.  
