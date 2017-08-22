---
title: "Tworzenie sekwencji zadań w celu zainstalowania systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Użyj sekwencji zadań w programie System Center Configuration Manager automatyczne zainstalowanie obrazu systemu operacyjnego i innej zawartości na komputerze docelowym."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 217c8a0e-5112-420e-a325-2a6d75326290
caps.latest.revision: "13"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 41aa6cf69a746f0ab67d804f1ee0c70db05d65ee
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-a-task-sequence-to-install-an-operating-system-in-system-center-configuration-manager"></a>Tworzenie sekwencji zadań instalacji systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj sekwencji zadań w programie System Center Configuration Manager, aby automatycznie zainstalować obrazu systemu operacyjnego na komputerze docelowym. Należy utworzyć sekwencję zadań odwołującą się do obrazu rozruchowego, który służy do uruchamiania komputera docelowego, do obrazu systemu operacyjnego, który ma zostać zainstalowany na komputerze docelowym, a także do innej dodatkowej zawartości, takiej jak inne aplikacje lub aktualizacje oprogramowania, które mają zostać zainstalowane. Następnie należy wdrożyć sekwencję zadań w kolekcji zawierającej komputer docelowy.  

##  <a name="BKMK_InstallOS"></a> Tworzenie sekwencji zadań instalacji systemu operacyjnego  
 Istnieje wiele scenariuszy wdrażania systemu operacyjnego na komputerach w danym środowisku. W większości przypadków należy utworzyć sekwencję zadań i wybrać pozycję **Zainstaluj istniejący pakiet obrazów** w Kreatorze tworzenia sekwencji zadań, aby zainstalować system operacyjny, przeprowadzić migrację ustawień użytkowników, zastosować aktualizacje oprogramowania i zainstalować aplikacje. Przed utworzeniem sekwencji zadań do zainstalowania systemu operacyjnego muszą być spełnione następujące warunki:   

-   **Wymagane**  

    -   [Obrazu rozruchowego](../get-started/manage-boot-images.md) muszą być dostępne w konsoli programu Configuration Manager.  

    -   [Obrazu systemu operacyjnego](../get-started/manage-operating-system-images.md) muszą być dostępne w konsoli programu Configuration Manager.  

-   **Wymagane (jeśli są używane)**  

    -   [Aktualizacje oprogramowania](../../sum/get-started/synchronize-software-updates.md) muszą być zsynchronizowane w konsoli programu Configuration Manager.  

    -   [Aplikacje](../../apps/deploy-use/create-applications.md) muszą zostać dodane do konsoli programu Configuration Manager.  

#### <a name="to-create-a-task-sequence-that-installs-an-operating-system"></a>Aby utworzyć sekwencję zadań instalacji systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Tworzenie nowej sekwencji zadań** kliknij pozycję **Zainstaluj istniejący pakiet obrazów**, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Informacje o sekwencji zadań** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa sekwencji zadań**: Określ nazwę identyfikującą sekwencję zadań.  

    -   **Opis elementu**: Określ opis zadania wykonywanego przez sekwencję zadań.  

    -   **Obraz rozruchowy**: Określ obraz rozruchowy, który instaluje system operacyjny na komputerze docelowym. Obraz rozruchowy zawiera wersję środowiska Windows PE, które służy do instalowania systemu operacyjnego, a także wymaganych dodatkowych sterowników urządzeń. Aby uzyskać informacje, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

        > [!IMPORTANT]  
        >  Architektura obrazu rozruchowego musi być zgodna z architekturą sprzętową komputera docelowego.  

6.  Na stronie **Instalowanie systemu Windows** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Pakiet obrazów**: Określ pakiet, który zawiera obraz systemu operacyjnego do zainstalowania. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  

    -   **Obraz**: Jeśli pakiet obrazu systemu operacyjnego zawiera wiele obrazów, określ indeks obrazu systemu operacyjnego do zainstalowania.  

    -   **Podziel na partycje i sformatuj dysk komputera docelowego instalującego system operacyjny**: Określ, czy sekwencja zadań na partycje i formatowania komputera docelowego przed zainstalowaniem systemu operacyjnego.  

    -   **Klucz produktu**: Określ klucz produktu systemu operacyjnego do zainstalowania. Możesz określić zakodowane klucze licencji zbiorczych oraz standardowe klucze produktów. W przypadku użycia niezakodowanego klucza produktu poszczególne grupy 5 znaków muszą być oddzielone kreskami (-). Na przykład: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Tryb licencjonowania serwera**: Określ, czy serwer licencji jest **na stanowisko**, **na serwer**, lub które nie licencji. W przypadku wybrania licencji serwera **Na serwer**określ również maksymalną liczbę połączeń serwera.  

    -   Określ, w jaki sposób ma być obsługiwane konto administratora używane podczas wdrażania obrazu systemu operacyjnego.  

        -   **Wyłącz konto administratora lokalnego**: Określ, czy wyłączyć konto administratora lokalnego po wdrożeniu obrazu systemu operacyjnego.  

        -   **Zawsze używaj tego samego hasła administratora**: Określ, czy jest używane to samo hasło dla konta administratora lokalnego na wszystkich komputerach z wdrożonym obrazem systemu operacyjnego.  

7.  Na stronie **Konfigurowanie sieci** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Przyłącz do grupy roboczej**: Określ, czy dodać komputer docelowy do grupy roboczej.  

    -   **Przyłącz do domeny**: Określ, czy dodać komputer docelowy do domeny. W polu **Domena**określ nazwę domeny.  

        > [!IMPORTANT]  
        >  W lesie lokalnym możesz przeglądać w poszukiwaniu domen, lecz w przypadku lasu zdalnego musisz określić nazwę domeny.  

         Możesz również określić jednostkę organizacyjną (OU). To jest ustawienie opcjonalne określające nazwę wyróżniającą LDAP X.500 jednostki OU, w której ma zostać utworzone konto komputera, jeżeli jeszcze nie istnieje.  

    -   **Konto**: Określ nazwę użytkownika i hasło dla konta, które ma uprawnienia do dołączenia do określonej domeny. Przykład: *domena\użytkownik* lub *%zmienna%*.  

        > [!IMPORTANT]  
        >  Aby przeprowadzić migrację ustawień domeny lub ustawień grupy roboczej, wprowadź odpowiednie poświadczenia domeny.  

8.  Na **Instalowanie programu Configuration Manager** Określ pakiet klienta programu Configuration Manager można zainstalować na komputerze docelowym, a następnie kliknij przycisk **dalej**.  

9. Na stronie **Migracja stanu** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Przechwyć ustawienia użytkownika**: Określ, czy sekwencja zadań ma przechwytywać stan użytkownika. Aby uzyskać więcej informacji o sposobie przechwytywania i przywracania stanu użytkownika, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

    -   **Przechwyć ustawienia sieci**: Określ, czy sekwencja zadań ma przechwytywać ustawienia sieci z komputera docelowego. Oprócz ustawień karty sieciowej można przechwycić członkostwo domeny lub grupy roboczej.  

    -   **Przechwyć ustawienia Microsoft Windows**:  Określ, czy sekwencja zadań ma przechwytywać ustawienia systemu Windows z komputera docelowego przed zainstalowaniem obrazu systemu operacyjnego. Można przechwycić nazwy komputera, zarejestrowanego użytkownika i organizacji oraz ustawienia strefy czasowej.  

10. Na stronie **Dołączanie aktualizacji** określ, czy instalować wymagane aktualizacje oprogramowania lub wszystkie aktualizacje, bądź nie instalować żadnych aktualizacji, a następnie kliknij przycisk **Dalej**. Po wybraniu opcji instalowania aktualizacji oprogramowania programu Configuration Manager instaluje tylko aktualizacje oprogramowania, które są przeznaczone do kolekcji, których członkiem jest komputer docelowy.  

11. Na stronie **Instalowanie aplikacji** określ aplikacje do zainstalowania na komputerze docelowym, a następnie kliknij przycisk **Dalej**. Jeżeli określisz wiele aplikacji, możesz również wybrać, aby nie przerywać sekwencji zadań w przypadku niepowodzenia instalowania określonej aplikacji.  

12. Ukończ pracę kreatora.  

 Teraz możesz wdrożyć sekwencję zadań w kolekcji komputerów.  Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

##  <a name="BKMK_InstallExistingOSImageTSExample"></a> Przykładowa sekwencja zadań powodująca zainstalowanie istniejącego obrazu systemu operacyjnego  
 W poniższej tabeli przedstawiono wskazówki pomocne podczas tworzenia sekwencji zadań w celu wdrożenia systemu operacyjnego przy użyciu istniejącego obrazu systemu operacyjnego. Informacje w tabeli pomogą w określeniu ogólnej sekwencji kroków sekwencji zadań oraz sposobu organizowania i definiowania struktury tych kroków sekwencji zadań w grupach logicznych. Tworzona sekwencja zadań może się różnić od tego przykładu i może zawierać więcej lub mniej grup i kroków sekwencji zadań.  

> [!IMPORTANT]  
>  Taką sekwencję zadań należy zawsze tworzyć przy użyciu Kreatora tworzenia sekwencji zadań.  

 W przypadku utworzenia nowej sekwencji zadań przy użyciu Kreatora tworzenia sekwencji zadań niektóre nazwy kroków sekwencji zadań różnią się od nazw kroków sekwencji zadań dodawanych ręcznie do istniejącej sekwencji zadań. Różnice nazewnictwa przedstawiono w poniższej tabeli:  

|Nazwa kroku sekwencji zadań w Kreatorze tworzenia sekwencji zadań|Równoważna nazwa kroku w edytorze sekwencji zadań|  
|---------------------------------------------------------|-----------------------------------------------|  
|Zażądaj magazynu stanów użytkownika|Zażądaj magazynu stanów|  
|Przechwyć pliki użytkownika i ustawienia|Przechwyć stan użytkownika|  
|Zwolnij magazyn stanów użytkownika|Zwolnij magazyn stanów|  
|Uruchom ponownie w systemie Windows PE|Wykonaj ponowny rozruch przy użyciu środowiska Windows PE lub dysku twardego|  
|Podziel dysk 0 na partycje|Formatuj dysk i podziel go na partycje|  
|Przywróć pliki użytkownika i ustawienia|Przywróć stan użytkownika|  

|Grupa lub krok sekwencji zadań|Opis|  
|---------------------------------|-----------------|  
|Przechwyć pliki i ustawienia — **(Nowa grupa sekwencji zadań)**|Umożliwia utworzenie grupy sekwencji zadań. Grupa sekwencji zadań zawiera podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.<br /><br /> Ta grupa zawiera kroki niezbędne do przechwytywania plików i ustawień z systemu operacyjnego komputera odniesienia.|  
|Przechwyć ustawienia systemu Windows|Ten krok sekwencji zadań służy do identyfikowania ustawień systemu Microsoft Windows do przechwycenia z komputera odniesienia. Można przechwycić nazwę komputera, informacje o użytkowniku i organizacji oraz ustawienia strefy czasowej.|  
|Przechwyć ustawienia sieci|Ten krok sekwencji zadań umożliwia przechwycenie ustawień sieci z komputera odniesienia. Oprócz ustawień karty sieciowej można przechwycić informacje o członkostwie w domenie lub grupie roboczej dla komputera odniesienia.|  
|Przechwyć pliki użytkownika i ustawienia — **(Nowa grupa sekwencji zadań podrzędnych)**|Utwórz grupę sekwencji zadań w innej grupie sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do przechwycenia danych stanu użytkownika. Tak jak w przypadku początkowo dodanej grupy, ta podgrupa zawiera podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.|  
|Zażądaj magazynu stanów użytkownika|Ten krok sekwencji zadań umożliwia zażądanie dostępu do punktu migracji stanu, w którym są przechowywane dane stanu użytkownika. Można skonfigurować ten krok sekwencji zadań do przechwytywania lub przywracania informacji o stanie użytkownika.|  
|Przechwyć pliki użytkownika i ustawienia|Użyj tego kroku sekwencji zadań Przechwyć stan użytkownika i ustawienia z komputera odniesienia, który otrzyma sekwencję zadań skojarzoną z tym krokiem zadania przy użyciu narzędzia migracji stanu użytkowników (USMT). Można przechwytywać opcje standardowe lub skonfigurować opcje do przechwytywania.|  
|Zwolnij magazyn stanów użytkownika|Ten krok sekwencji zadań umożliwia powiadomienie punktu migracji stanu o ukończeniu akcji przechwytywania lub przywracania.|  
|Zainstaluj System operacyjny — **(Nowa grupa sekwencji zadań)**|Utwórz następną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do zainstalowania i skonfigurowania środowiska Windows PE.|  
|Uruchom ponownie w systemie Windows PE|Ten krok sekwencji zadań umożliwia określenie opcji ponownego uruchamiania komputera, który odbiera tę sekwencję zadań. Ten krok zapewnia wyświetlenie użytkownikowi komunikatu z informacją o ponownym uruchomieniu komputera, aby umożliwić kontynuowanie instalacji.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSInWinPE** . Jeśli skojarzona wartość jest równa **false** , ten krok sekwencji zadań jest kontynuowany.|  
|Podziel dysk 0 na partycje|Ten krok sekwencji zadań umożliwia określenie akcji niezbędnych do sformatowania dysku twardego na komputerze docelowym. Domyślny numer dysku to **0**.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSClientCache** . Ten krok zostanie uruchomiony, jeśli pamięć podręczna klienta programu Configuration Manager nie istnieje.|  
|Zastosuj system operacyjny|Ten krok sekwencji zadań umożliwia zainstalowanie obrazu systemu operacyjnego na komputerze docelowym. Ten krok należy wykonać wszystkie obrazy woluminów zawarte w pliku WIM do odpowiednich sekwencyjnych woluminów dysku na komputerze docelowym po wcześniejszym usunięciu wszystkich plików w danym woluminie (z wyjątkiem plików sterowania specyficzne dla programu Configuration Manager). Można określić plik odpowiedzi **SYSPREP** , a także skonfigurować partycję dysku do użycia podczas instalacji.|  
|Zastosuj ustawienia systemu Windows|Ten krok sekwencji zadań umożliwia skonfigurowanie informacji o konfiguracji ustawień systemu Windows dla komputera docelowego. Ustawienia systemu Windows, które można zastosować, to informacje o użytkownikach i organizacji, informacje o kluczu produktu lub licencji, strefa czasowa i hasło administratora lokalnego.|  
|Zastosuj ustawienia sieci|Ten krok sekwencji zadań pozwala określić informacje o konfiguracji sieci lub grupy roboczej dla komputera docelowego. Można również określić, czy komputer korzysta z serwera DHCP, lub statycznie przypisać informacje o adresie IP.|  
|Zastosuj sterowniki urządzeń|Ten krok sekwencji zadań umożliwia zainstalowanie sterowników w ramach wdrażania systemu operacyjnego. Możesz zezwolić Instalatorowi systemu Windows na przeszukanie wszystkich istniejących kategorii sterowników, wybierając pozycję **Uwzględnij sterowniki z wszystkich kategorii** , lub ograniczyć kategorie sterowników przeszukiwane przez Instalatora systemu Windows, wybierając pozycję **Ogranicz dopasowywanie tylko do sterowników z wybranych kategorii**.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSMediaType** . Ten krok sekwencji jest wykonywany tylko wtedy, gdy wartość zmiennej nie jest równa **FullMedia**.|  
|Zastosuj pakiet sterowników|Ten krok sekwencji zadań pozwala udostępnić wszystkie sterowniki urządzeń w pakiecie sterowników dostępnym do użycia podczas instalacji systemu Windows.|  
|Konfiguracja systemu operacyjnego - **(Nowa grupa sekwencji zadań)**|Utwórz następną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do skonfigurowania zainstalowanego systemu operacyjnego.|  
|Zainstaluj system Windows i program ConfigMgr|Ten krok sekwencji zadań należy zainstalować oprogramowanie klienta programu Configuration Manager. Configuration Manager instaluje i rejestruje identyfikator GUID klienta programu Configuration Manager. Niezbędne parametry instalacji można przypisać w oknie **Właściwości instalacji** .|  
|Zainstaluj aktualizacje|Ten krok sekwencji zadań umożliwia określenie sposobu instalacji aktualizacji oprogramowania na komputerze docelowym. Komputer docelowy nie jest sprawdzany pod kątem dostępności odpowiednich aktualizacji oprogramowania do czasu uruchomienia tego kroku sekwencji zadań. W tym momencie komputer docelowy sprawdzania pod kątem aktualizacji oprogramowania jak inny klient zarządzany przez Menedżera konfiguracji.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSMediaType** . Ten krok sekwencji jest wykonywany tylko wtedy, gdy wartość zmiennej nie jest równa **FullMedia**.|  
|Przywróć pliki użytkownika i ustawienia — **(Nowa grupa sekwencji zadań podrzędnych)**|Utwórz następną podgrupę sekwencji zadań. Ta podgrupa zawiera kroki niezbędne do przywrócenia plików użytkownika i ustawień.|  
|Zażądaj magazynu stanów użytkownika|Ten krok sekwencji zadań umożliwia zażądanie dostępu do punktu migracji stanu, w którym są przechowywane dane stanu użytkownika.|  
|Przywróć pliki użytkownika i ustawienia|Ten krok sekwencji zadań umożliwia zainicjowanie narzędzia migracji stanu (USMT) użytkownika, do przywrócenia stanu i ustawień użytkownika na komputerze docelowym.|  
|Zwolnij magazyn stanów użytkownika|Ten krok sekwencji zadań umożliwia powiadomienie punktu migracji stanu o tym, że dane stanu użytkownika nie są już potrzebne.|  
