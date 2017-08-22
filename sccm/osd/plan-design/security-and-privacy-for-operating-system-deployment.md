---
title: "Bezpieczeństwo i ochrona prywatności dotyczące wdrażania systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o zabezpieczeniach i prywatności najlepsze rozwiązania dotyczące wdrażania systemu operacyjnego w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5ee5928f-3d72-4b00-8156-1e0d1030a96c
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 5632a753fc565312a80b2ed69ce438335b3fad50
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-operating-system-deployment-in-system-center-configuration-manager"></a>Bezpieczeństwo i ochrona prywatności przy wdrażaniu systemów operacyjnych w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera bezpieczeństwa i informacje o ochronie prywatności dotyczące wdrażania systemu operacyjnego w programie System Center Configuration Manager.  

##  <a name="BKMK_Security_HardwareInventory"></a>Najlepsze rozwiązania dotyczące wdrażania systemu operacyjnego  
 Podczas wdrażania systemów operacyjnych w programie Configuration Manager, należy użyć poniższe najlepsze rozwiązania:  

-   **Wdrożenie kontroli dostępu w celu ochrony nośnika rozruchowego**  

     Tworząc nośnik rozruchowy, należy zawsze zabezpieczyć go hasłem. Jednak nawet w przypadku podania hasła szyfrowane są tylko pliki zawierające informacje poufne i wszystkie pliki mogą zostać nadpisane.  

     Należy kontrolować fizyczny dostęp do nośnika, aby uniemożliwić ataki kryptograficzne w celu uzyskania certyfikatu uwierzytelniania klienta.  

     Aby klient nie zainstalował zawartości lub zasad klienta, które zostały zmodyfikowane, dla zawartości jest wyznaczany skrót i trzeba jej używać z oryginalnymi zasadami.  Jeśli mieszanie zawartości lub sprawdzenie czy zawartość odpowiada zasadzie nie powiedzie się, klient nie będzie korzystał z nośnika rozruchowego. Mieszana jest tylko zawartość; zasada jest natomiast szyfrowana i zabezpieczona podanym hasłem, co utrudnia jej zmodyfikowanie przez atakującego.  

-   **Użyj zabezpieczonej lokalizacji, podczas tworzenia nośnika obrazów systemu operacyjnego**  

     Jeśli do lokalizacji będą mieli dostęp nieautoryzowani użytkownicy, będą mogli zmodyfikować tworzone pliki, a także zająć całe dostępne miejsce, uniemożliwiając utworzenie nośnika.  

-   **Chroń pliki certyfikatu (pfx) przy użyciu silnego hasła, a jeśli będą przechowywane w sieci, należy zabezpieczyć kanał sieciowy po zaimportowaniu do programu Configuration Manager**  

     Stosowanie hasła do importowania certyfikatu uwierzytelniania klienta, który jest używany dla nośnika rozruchowego, ułatwia ochronę certyfikatów przez atakującymi.  

     Aby zapobiec naruszeniu pliku certyfikatu przez atakującego, należy korzystać z podpisywania SMB lub ochrony IPsec między lokalizacją sieciową a serwerem lokacji.  

-   **Jeśli certyfikat klienta zostanie naruszony, należy go zablokować z programu Configuration Manager i odwołać, jeśli jest certyfikatem PKI**  

     Aby wdrożyć system operacyjny przy użyciu nośnika rozruchowego i rozruchu w środowisku PXE, należy mieć certyfikat uwierzytelniania klienta z kluczem prywatnym. Jeśli ten certyfikat zostanie naruszony, należy go zablokować w węźle **Certyfikaty**w obszarze roboczym **Administracja**, węzeł **Zabezpieczenia**.  

-   **Gdy dostawca programu SMS znajduje się na komputerze lub komputerach innych niż serwer lokacji, należy zabezpieczyć kanał komunikacji w celu ochrony obrazów rozruchowych**  

     Gdy obrazy rozruchowe są modyfikowane, a dostawca programu SMS jest uruchomiony na serwerze, który nie jest serwerem lokacji, obrazy rozruchowe są narażone na atak. Kanał sieciowy między tymi komputerami należy chronić za pomocą podpisywania SMB lub ochrony IPsec.  

-   **Włącz punkty dystrybucji dla komunikacji z klientami PXE tylko w chronionych segmentach sieci**  

     Gdy klient wyśle żądanie rozruchu w środowisku PXE, nie można w żaden sposób zapewnić, że żądanie zostanie obsłużone przez prawidłowy punkt dystrybucji obsługujący środowisko PXE. Taki scenariusz niesie ze sobą następujące zagrożenia bezpieczeństwa:  

    -   Nieautoryzowany punkt dystrybucji, który odpowiada na żądania PXE może dostarczyć klientom zmodyfikowany obraz.  

    -   Atakujący może rozpocząć atak typu man-in-the-middle skierowany na protokół TFTP stosowany przez usługę PXE i wysłać złośliwy kod z plikami systemu operacyjnego. Może także utworzyć nieautoryzowanego klienta, który będzie wysyłał żądania TFTP bezpośrednio do punktu dystrybucji.  

    -   Atakujący może użyć złośliwego klienta w celu uruchomienia ataku typu „odmowa usługi” nakierowanego na punkt dystrybucji.  

     Aby chronić segmenty sieci, w których klienci będą mieli dostęp do punktów dystrybucji żądań PXE, należy korzystać z rozbudowanej ochrony.  

    > [!WARNING]  
    >  Z powodu tych zagrożeń bezpieczeństwa nie należy włączać punktu dystrybucji dla komunikacji środowiska PXE, gdy znajduje się w niezaufanej sieci, takiej jak na przykład sieć obwodowa.  

-   **Konfigurowanie punktów dystrybucji z włączoną obsługą środowiska PXE do odpowiadania na żądania środowiska PXE tylko na określonych interfejsach sieciowych**  

     Zezwolenie punktowi dystrybucji na odpowiadanie na wszystkie żądania PXE na wszystkich interfejsach sieciowym może uwidocznić usługę PXE niezaufanym sieciom  

-   **Wymagaj hasła do rozruchu w środowisku PXE**  

     Żądanie hasła do rozruchu w środowisku PXE, ta konfiguracja dodaje kolejny poziom zabezpieczeń do procesu rozruchu PXE, aby ułatwić ochronę przed nieautoryzowanymi klientami dołączającymi do hierarchii programu Configuration Manager.  

-   **Nie należy umieszczać aplikacji branżowych lub oprogramowania zawierającego poufne dane do obrazu, który będzie używany do rozruchu w środowisku PXE lub multiemisji**  

     Z powodu nieuniknionych zagrożeń bezpieczeństwa związanych z rozruchem w środowisku PXE i multiemisją należy zmniejszyć zagrożenie, jeśli nieautoryzowany komputer pobierze obraz systemu operacyjnego.  

-   **Nie należy umieszczać aplikacji branżowych lub oprogramowania zawierającego poufne dane zawarte w pakiety oprogramowania, które są instalowane przy użyciu zmiennych sekwencji zadań**  

     Podczas wdrażania pakietów oprogramowania przy użyciu zmiennych sekwencji zadań oprogramowanie może zostać zainstalowane na komputerach oraz dla użytkowników niemających uprawnień do jego otrzymania.  

-   **Podczas migracji stanu użytkownika należy zabezpieczyć kanał sieciowy między klientem a punktem migracji stanu za pomocą podpisywania SMB lub protokołu IPsec**  

     Po początkowym nawiązaniu połączenia za pośrednictwem protokołu HTTP, dane migracji stanu użytkownika są transferowane przy użyciu bloków SMB.  Jeśli kanał sieciowy nie zostanie zabezpieczony, atakujący będzie mógł odczytać i zmodyfikować te dane.  

-   **Użyj najnowszej wersji programu stanu użytkowników migracji narzędzia (USMT) obsługującego programu Configuration Manager**  

     Najnowsza wersja narzędzia USMT zawiera ulepszenia zabezpieczeń oraz zapewnia lepszą kontrolę w przypadku migracji danych stanu użytkownika.  

-   **Ręcznie usuń foldery w punkcie migracji stanu zlikwidowane**  

     Po usunięciu folderu punktu migracji stanu w konsoli programu Configuration Manager we właściwościach punktu migracji stanu nie powoduje usunięcia folderu fizycznego. Aby zabezpieczyć dane migracji stanu użytkownika przed ujawnieniem informacji, należy ręcznie usunąć udział sieciowy i folder.  

-   **Nie należy konfigurować zasad usuwania można natychmiast usunąć stan użytkownika**  

     Jeśli zasady usuwania w punkcie migracji stanu zostaną skonfigurowane tak, aby dane oznaczone do usunięcia były usuwane natychmiast, i jeśli atakujący uzyska dane stanu użytkownika nim uzyska je odpowiedni komputer, dane stanu użytkownika zostaną natychmiast usunięte. Ustaw interwał **Usuń po**, aby był wystarczająco długi, by dało się zweryfikować przywrócone dane stanu użytkownika.  

-   **Ręcznie Usuń skojarzenia komputera po i zweryfikowaniu przywracanie danych migracji stanu użytkownika**  

     Menedżer konfiguracji nie są automatycznie usuwane powiązania komputerów. Ochrona danych stanu użytkownika przez ręczne usunięcie skojarzeń komputera nie jest już wymagana.  

-   **Ręczne tworzenie kopii zapasowej danych migracji stanu użytkownika w punkcie migracji stanu**  

     Kopia zapasowa programu Configuration Manager nie uwzględnia danych migracji stanu użytkownika.  

-   **Pamiętaj, aby włączyć funkcję BitLocker po zainstalowaniu systemu operacyjnego**  

     Jeśli komputer obsługuje funkcję BitLocker, musisz ją wyłączyć za pomocą kroku sekwencji zadań, jeśli chcesz przeprowadzić dyskretną instalację systemu operacyjnego. Menedżer konfiguracji nie włącza funkcji BitLocker po zainstalowaniu systemu operacyjnego, więc musi ponownego, ręcznego włączenia funkcji BitLocker.  

-   **Wdrożenie kontroli dostępu w celu ochrony wstępnie przygotowanego nośnika**  

     Należy kontrolować fizyczny dostęp do nośnika, aby uniemożliwić ataki kryptograficzne w celu uzyskania certyfikatu uwierzytelniania klienta i poufnych danych.  

-   **Wdrożenie kontroli dostępu w celu ochrony procesu tworzenia obrazu komputera odniesienia**  

     Upewnij się, że komputer wzorcowy służący do przechwytywania obrazów systemu operacyjnego jest w bezpiecznym środowisku z odpowiednią kontrolą dostępu, tak aby nie dało się zainstalować nieoczekiwanego lub złośliwego oprogramowania albo nieumyślnie przypadkowo go w przechwytywanym obrazie. Przechwytując obraz, upewnij się, że lokalizacja udziału plików w sieci docelowej jest bezpieczna, tak aby nie dało się zmodyfikować obrazu po jego przechwyceniu.  

-   **Zawsze instaluj najnowsze aktualizacje zabezpieczeń na komputerze odniesienia**  

     Gdy na komputerze wzorcowym znajdują się bieżące aktualizacje zabezpieczeń, stopień narażenia nowych komputerów jest mniejszy przy ich pierwszym uruchomieniu.  

-   **Jeśli zachodzi potrzeba wdrożenia systemów operacyjnych na nieznanym komputerze, należy zaimplementować kontrolę dostępu, aby nieautoryzowane komputery z połączeniem z siecią**  

     Choć inicjowanie obsługi nieznanych komputerów stanowi wygodną metodę wdrażania nowych komputerów na żądania, może także spowodować, że atakujący stanie się zaufanym klientem w sieci. Ogranicz dostęp fizyczny do sieci i monitoruj klientów w celu wykrywania nieautoryzowanych komputerów. Komputery odpowiadające na wdrożenie systemu operacyjnego zainicjowanego przez środowisko PXE mogą podczas wdrażania systemu operacyjnego utracić wszystkie dane, co zaowocuje utratą dostępności przypadkowo ponownie sformatowanych systemów.  

-   **Włącz szyfrowanie pakietów multiemisji**  

     Dla każdego pakietu wdrożenia systemu operacyjnego istnieje możliwość włączenia szyfrowania, przesyłania Menedżera konfiguracji pakietu przy użyciu multiemisji. Ta konfiguracja uniemożliwia nieautoryzowanym komputerom dołączenie do sesji multiemisji i zapobiega modyfikowaniu transmisji przez atakujących.  

-   **Monitor dla punktów dystrybucji obsługujących multiemisję nieautoryzowanego**  

     Jeśli atakujący mogą uzyskać dostęp do sieci, mogą skonfigurować nieautoryzowane serwery multiemisji, tak aby podszywały się pod wdrożenie systemu operacyjnego.  

-   **Podczas eksportowania sekwencji zadań do lokalizacji sieciowej, Zabezpiecz lokalizację i kanał sieciowy**  

     Ogranicz dostęp użytkowników do danego folderu sieciowego.  

     Aby zapobiec naruszeniu eksportowanej sekwencji zadań przez atakującego, należy korzystać z podpisywania SMB lub ochrony IPsec między lokalizacją sieciową a serwerem lokacji.  

-   **Kanał komunikacyjny używany podczas przekazywania wirtualnego dysku twardego do programu Virtual Machine Manager.**  

     Aby zapobiec modyfikowaniu danych podczas transferu w sieci, należy użyć zabezpieczeń protokołu internetowego (IPsec) lub blok komunikatów serwera (SMB) między komputera, na którym jest uruchomiona konsola programu Configuration Manager, a komputerem z programem Virtual Machine Manager.  

-   **Jeśli należy użyć zadania konta Uruchom jako sekwencji, należy zastosować dodatkowe zabezpieczenia**  

     Korzystając z konta Uruchom jako sekwencji zadań, należy wykonać następujące czynności zaradcze:  

    -   Użyj konta z najmniejszymi możliwymi uprawnieniami.  

    -   Nie używaj na tym koncie konta dostępu do sieci.  

    -   Nigdy nie konfiguruj konta administratorem domeny.  

     Ponadto:  

    -   Nigdy nie konfiguruj profilów mobilnych dla tego konta. Po uruchomieniu sekwencji zadań pobiera ona profil mobilny dla konta, co sprawia, że profil jest narażony na dostęp na komputerze lokalnym.  

    -   Ogranicz zakres konta. Utwórz na przykład różne konta Uruchom jako dla poszczególnych sekwencji zadań. W przypadku złamania zabezpieczeń jednego konta zostaną złamane wyłącznie zabezpieczenia komputerów klienckich, do których to konto ma dostęp. Jeśli wiersz polecenia wymaga dostępu administracyjnego na komputerze, na wszystkich komputerach uruchamiających sekwencję zadań możesz utworzyć konta administratora lokalnego przeznaczone wyłącznie na potrzeby konta Uruchom jako sekwencji zadań, a następnie usunąć te konta, gdy tylko nie będą potrzebne.  

-   **Ogranicz i Monitoruj użytkowników administracyjnych, którym nadano rolę zabezpieczeń Menedżera wdrożenia systemu operacyjnego**  

     Użytkownicy administracyjni, którym nadano rolę zabezpieczeń Menedżera wdrożenia systemu operacyjnego mogą tworzyć certyfikaty z podpisem własnym, które można następnie używane do personifikowania klienta i Uzyskaj zasady klienta z programu Configuration Manager.  

### <a name="security-issues-for-operating-system-deployment"></a>Problemy z zabezpieczeniami dotyczące wdrożeń systemu operacyjnego  
 Choć wdrożenie systemu operacyjnego może być wygodną metodą wdrożenia najbezpieczniejszych systemów operacyjnych i konfiguracji na komputerach w sieci, niesie ze sobą następujące niebezpieczeństwa:  

-   Ujawnienie informacji i odmowa obsługi  

     Jeśli osoba atakująca może uzyskać kontrolę nad infrastruktury programu Configuration Manager, może uruchomić sekwencje zadań uwzględniające formatowanie dysków twardych wszystkich komputerów klienckich. Sekwencje zdań można skonfigurować tak, aby zawierały poufne dane, takie jak na przykład informacje o kontach z uprawnieniami do dołączania domeny czy klucze licencji zbiorczej.  

-   Personifikacja i podniesienie uprawnień  

     Sekwencje zadań mogą dołączyć komputer do domeny, co może zapewnić nieautoryzowanemu komputerowi uwierzytelniony dostęp do sieci. Innym ważnym zagadnieniem dotyczącym zabezpieczeń wdrożenia systemu operacyjnego jest ochrona certyfikatu uwierzytelniania klienta dla rozruchowego nośnika sekwencji zadań i wdrożenia rozruchu w środowisku PXE. Przechwycenie certyfikatu uwierzytelniania klienta daje atakującemu możliwość uzyskania klucza prywatnego z certyfikatu, a następnie personifikację prawidłowego klienta w sieci.  

     Jeśli osoba atakująca uzyskuje certyfikat klienta używany z rozruchowym nośnikiem sekwencji zadań oraz wdrożenia rozruchu środowiska PXE, ten certyfikat może służyć do podszyć się pod prawidłowego klienta w programie Configuration Manager. W tym scenariuszu nieautoryzowany komputer może pobrać zasadę, która może zawierać dane poufne.  

     Jeśli klienci używają konta dostępu do sieci w celu uzyskiwania dostępu do danych przechowywanych w punkcie migracji stanu, mogą oni efektywnie współużytkować tę samą tożsamość oraz mieć dostęp do danych migracji stanu z innego klienta używającego konta dostępu do sieci. Dane są szyfrowane, więc może je odczytać tylko oryginalny klient. Mogą jednak zostać naruszone lub usunięte.  

-   Uwierzytelnianie klienta w punkcie migracji stanu jest realizowane za pośrednictwem tokenu programu Configuration Manager wydawanego przez punkt zarządzania.  

     Ponadto programu Configuration Manager nie ograniczyć lub zarządzać ilość danych przechowywanych w punkcie migracji stanu i osoba atakująca może zapełnić dostępne miejsce na dysku i spowodować typu "odmowa usługi".  

-   W przypadku używania zmiennych kolekcji lokalni administratorzy mogą odczytać potencjalnie wrażliwe informacje.  

     Mimo że zmienne kolekcji oferują elastyczną metodą wdrażania systemów operacyjnych, może to skutkować ujawnieniem informacji.  

##  <a name="BKMK_Privacy_HardwareInventory"></a>Informacje o ochronie prywatności dotyczące wdrażania systemu operacyjnego  
 Oprócz wdrażania systemów operacyjnych na komputerach bez systemu operacyjnego, programu Configuration Manager może służyć do migracji ustawień i plików użytkowników z jednego komputera na inny. Administrator konfiguruje, które informacje mają być przesłane, takie jak pliki danych osobistych, ustawienia konfiguracyjne i pliki cookie przeglądarki.  

 Informacje są przechowywane w punkcie migracji stanu i szyfrowane podczas transmisji i przechowywania. Informacje mogą być pobierane przez nowy komputer skojarzony z informacjami o stanie. Jeśli nowy komputer straci klucz pozwalający pobierać informacje, administrator programu Configuration Manager z uprawnieniem Wyświetl informacje odzyskiwania względem obiektów wystąpienia skojarzenia komputera może uzyskać dostęp do informacji i skojarzyć je z nowym komputerem. Gdy nowy komputer przywróci informacje o stanie, domyślnie usunie je po jednym dniu. Można skonfigurować, kiedy punkt migracji stanu usuwa dane oznaczone do usunięcia. Informacje o migracji stanu nie są przechowywane w bazie danych lokacji ani nie są wysyłane do firmy Microsoft.  

 W przypadku wdrażania obrazów systemu operacyjnego za pomocą nośników rozruchowych należy zawsze używać domyślnej opcji zabezpieczania nośnika hasłem. Hasło szyfruje wiele zmiennych przechowywanych w sekwencji zadań, jednak wszystkie informacje, które nie są przechowywane w zmiennej, mogą stać się podatne na ujawnienie.  

 Wdrożenie systemu operacyjnego może wykorzystywać sekwencje zadań do wykonywania wielu różnych zadań procesu wdrożenia, takich jak instalowanie aplikacji i aktualizowanie oprogramowania. Podczas konfigurowania sekwencji zadań należy pamiętać o kwestiach prywatności związanych z instalacją oprogramowania.  

 W przypadku przekazywania wirtualnego dysku twardego do Menedżera maszyny wirtualnej bez uprzedniego wyczyszczenia obrazu programem Sysprep przekazany wirtualny dysk twardy może zawierać dane osobiste z oryginalnego obrazu.  

 Menedżer konfiguracji nie implementuje wdrożenia systemu operacyjnego domyślnie i przed zbieranie informacji o stanie użytkownika lub tworzenia sekwencji zadań lub obrazów rozruchowych wymaga podjęcia kilku czynności konfiguracyjnych.  

 Przed skonfigurowaniem wdrożenia systemu operacyjnego należy wziąć pod uwagę wymogi związane z ochroną prywatności.  
