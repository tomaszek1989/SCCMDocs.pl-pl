---
title: "Zarządzanie systemem Windows jako usługą — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Wyświetlać stan systemu Windows jako usługą za pomocą programu Configuration Manager, tworzyć plany obsługi w celu zdefiniowania pierścieni wdrażania i wyświetlać alerty, gdy zbliża się koniec obsługi klientów systemu Windows 10."
ms.custom: na
ms.date: 03/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da1e687b-28f6-43c4-b14a-ff2b76e60d24
caps.latest.revision: "26"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: fe02981433482ebf6880feec3e1822e6e8f4550f
ms.sourcegitcommit: 31c670a4bce74fd64a7d46ebf7702f65b80d4147
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2017
---
# <a name="manage-windows-as-a-service-using-system-center-configuration-manager"></a>Zarządzanie systemem Windows jako usługą za pomocą programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 W programie System Center Configuration Manager, można wyświetlać stan systemu Windows jako usługi w danym środowisku, tworzyć plany obsługi w celu zdefiniowania pierścieni wdrażania i sprawdź, czy systemu Windows 10 bieżącej gałęzi, które systemy są aktualizowane podczas nowe kompilacje są wydawane i wyświetlać alerty, gdy klientów systemu Windows 10 zbliża się koniec obsługi kompilacji Current Branch (CB) lub Current Branch for Business (CBB).  

 Aby uzyskać więcej informacji na temat opcji obsługi systemu Windows 10, zobacz  [Opcje obsługi systemu Windows 10 dotyczące aktualizacji i uaktualnień](https://technet.microsoft.com/library/mt598226\(v=vs.85\).aspx).  

 Poniższe sekcje umożliwiają zarządzanie systemem Windows jako usługi.

##  <a name="BKMK_Prerequisites"></a> Wymagania wstępne  
 Aby można było wyświetlać dane na pulpicie nawigacyjnym obsługi systemu Windows 10, muszą być spełnione następujące warunki:  

-   Komputery z systemem Windows 10 muszą używać aktualizacji oprogramowania programu Configuration Manager z systemu Windows Server Update Services (WSUS) do zarządzania aktualizacjami oprogramowania. Jeśli komputery używają usługi Windows Update dla Firm (lub dla niejawnych testerów systemu Windows) do zarządzania aktualizacjami oprogramowania, komputer nie zostanie oceniony w planach obsługi systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Integracja z usługą Windows Update dla Firm w systemie Windows 10](../../sum/deploy-use/integrate-windows-update-for-business-windows-10.md).  

-   Program WSUS 4.0 z [poprawką 3095113](https://support.microsoft.com/kb/3095113) musi być zainstalowany w punktach aktualizacji oprogramowania i na serwerach lokacji. Powoduje to dodanie klasyfikacji aktualizacji oprogramowania **Uaktualnienia** . Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące aktualizacji oprogramowania](../../sum/plan-design/prerequisites-for-software-updates.md).  

-   Program WSUS 4.0 z [poprawkę 3159706](https://support.microsoft.com/kb/3159706) musi być zainstalowany w punktach aktualizacji oprogramowania i serwery do uaktualnienia komputerów z systemem Windows 10 Anniversary aktualizacji, a także wersje podsekwencji lokacji. Są wymagane ręczne wykonanie czynności opisanych w artykule pomocy technicznej, że należy wykonać, aby zainstalować tę poprawkę. Aby uzyskać więcej informacji, zobacz [pakietu Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/2016/08/05/update-your-configmgr-1606-sup-servers-to-deploy-the-windows-10-anniversary-update/).

-   Włącz odnajdywanie pulsu. Dane wyświetlane na pulpicie nawigacyjnym obsługi systemu Windows 10 są wyszukiwane przy użyciu odnajdywania. Aby uzyskać więcej informacji, zobacz [Konfigurowanie odnajdywania pulsu](../../core/servers/deploy/configure/configure-discovery-methods.md#BKMK_ConfigHBDisc).  

     Następujące informacje dotyczące gałęzi i kompilacji systemu Windows 10 są odnajdywane i przechowywane w następujących atrybutach:  

    -   **Gałąź gotowości systemu operacyjnego**: Określa gałąź systemu operacyjnego. Na przykład **0** = CB (nie odraczaj uaktualnień), **1** = CBB (odroczenie uaktualnień), **2** = Long Term Servicing Branch (LTSB)

    -   **Kompilacji systemu operacyjnego**: Określony kompilacji systemu operacyjnego. Na przykład **10.0.10240** (RTM) lub **10.0.10586** (wersja 1511)  

-   Punkt połączenia z usługą musi być zainstalowany i skonfigurowany dla trybu **Online, połączenie trwałe** , aby można było wyświetlać dane na pulpicie nawigacyjnym obsługi systemu Windows 10. Podczas pracy w trybie offline, należy aktualizacje nie będą wyświetlane dane na pulpicie nawigacyjnym do momentu uzyskania aktualizacji obsługi programu Configuration Manager.   
     Aby uzyskać więcej informacji, zobacz [o punkt połączenia z usługą](../../core/servers/deploy/configure/about-the-service-connection-point.md).  


-   Na komputerze, na którym jest uruchomiona konsola programu Configuration Manager musi być zainstalowany program Internet Explorer 9 lub nowszy.  

-   Aktualizacje oprogramowania muszą być skonfigurowane i zsynchronizowane. Musisz wybrać **uaktualnień** klasyfikacji i zsynchronizować aktualizacje oprogramowania, które uaktualnienia funkcji systemu Windows 10 będą dostępne w konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [przygotowanie do oprogramowania aktualizuje zarządzania](../../sum/get-started/prepare-for-software-updates-management.md).  

##  <a name="BKMK_ServicingDashboard"></a> Pulpit nawigacyjny obsługi systemu Windows 10  
 Pulpit nawigacyjny obsługi systemu Windows 10 zapewnia informacje o komputerach z systemem Windows 10 w danym środowisku, aktywnych planach obsługi, zgodności itd. Dane na pulpicie nawigacyjnym obsługi systemu Windows 10 są zależne od tego, czy jest zainstalowany punkt połączenia z usługą. Pulpit nawigacyjny zawiera następujące kafelki:  

-   **Kafelek użycie systemu Windows 10**:  Zawiera podział publicznych kompilacji systemu Windows 10. Kompilacje dla niejawnych testerów systemu Windows są wymienione jako **inne** , podobnie jak wszelkie kompilacje, które nie są jeszcze znane w danej lokacji. Punkt połączenia z usługą pobierze metadane, które zawierają informacje o kompilacjach systemu Windows. Następnie te dane zostaną porównane z danymi odnajdywania.  

-   **Kafelek pierścienie systemu Windows 10**:  Zawiera podział systemu Windows 10 według gałęzi i stanu gotowości. LTSB segment będą wszystkie wersje LTSB (natomiast pierwszy Kafelek zawiera podział według określonych wersji. Na przykład systemu Windows 10 LTSB 2015. Segment **Release Ready** odpowiada gałęzi CB, a segment **Business Ready** odpowiada gałęzi CBB.  

-   **Tworzenie planu Service kafelka**:   Umożliwia szybkie utworzenie planu obsługi. Należy określić nazwę, kolekcję (wyświetlanych jest tylko pierwszych dziesięć kolekcji według rozmiaru, od najmniejszego), pakiet wdrożeniowy (wyświetlanych jest tylko pierwszych dziesięć pakietów w kolejności od ostatnio zmodyfikowanego) i stan gotowości. Dla innych ustawień są używane wartości domyślne. Kliknij pozycję **Ustawienia zaawansowane** , aby uruchomić Kreatora tworzenia planu obsługi, za pomocą którego można skonfigurować wszystkie ustawienia planu obsługi.  

-   **Kafelek wygasłe**: Przedstawia wartość procentową urządzeń używających kompilacji systemu Windows 10, która osiągnęła koniec cyklu życia. Configuration Manager określa wartość procentową na podstawie metadanych pobiera punkt połączenia z usługą i porównuje ją z danymi odnajdywania. Kompilacja, która osiągnęła koniec cyklu życia, nie otrzymuje już comiesięcznych aktualizacji zbiorczych, w tym aktualizacji zabezpieczeń. Komputery z tej kategorii powinny zostać uaktualnione do następnej wersji kompilacji. Zaokrągla programu Configuration Manager w górę do najbliższej liczby całkowitej. Jeśli na przykład istnieje 10000 komputerów i tylko na jednym jest używana wygasła kompilacja, na kafelku będzie wyświetlana wartość 1%.  

-   **Kafelek wkrótce wygaśnie**: Wyświetla procent komputerów używających kompilacji, która wkrótce osiągnie koniec cyklu życia (w ciągu około czterech miesięcy), podobnie jak **wygasłe** kafelka. Zaokrągla programu Configuration Manager w górę do najbliższej liczby całkowitej.  

-   **Kafelek alerty**: Przedstawia aktywne alerty.  

-   **Kafelek monitorowanie planu obsługi**: Zostały utworzone plany obsługi i wykres zgodności dla każdego. Zapewnia to szybki przegląd bieżącego stanu wdrożeń planu obsługi. Jeśli wcześniejszy pierścień wdrażania spełnia oczekiwania dotyczące zgodności, możesz wybrać późniejszy plan obsługi (pierścień wdrażania) i kliknąć pozycję **Wdróż teraz** , zamiast czekać na automatyczne wyzwolenie reguł planu obsługi.  

-   **Kafelek kompilacje systemu Windows 10**:  Wyświetlana jest czasu Stały obraz wiersza, który zapewnia możesz kompilacje Przegląd systemu Windows 10, które obecnie są wydawane i udostępnia ogólne informacje o tym, kiedy kompilacje przejdą do innych stanów.  

> [!IMPORTANT]  
>  Informacje wyświetlane na pulpicie nawigacyjnym obsługi systemu Windows 10 (na przykład cykl pomocy technicznej dla wersji systemu Windows 10) są udostępniane dla wygody użytkownika i tylko do użytku wewnętrznego w firmie. Nie należy polegać wyłącznie na tych informacjach w celu potwierdzenia zgodności aktualizacji. Należy sprawdzać prawidłowość udostępnianych informacji.  

## <a name="servicing-plan-workflow"></a>Przepływ pracy planu obsługi  
 Plany obsługi systemu Windows 10 w programie Configuration Manager są podobne do reguł automatycznego wdrażania dla aktualizacji oprogramowania. Plan obsługi jest tworzony z następującymi kryteriami, które program Configuration Manager ocenia:  

-   **Klasyfikacja uaktualnienia**: Tylko te aktualizacje, które znajdują się w **uaktualnień** klasyfikacji są oceniane.  

-   **Stan gotowości**: Stan gotowości zdefiniowany w planie obsługi jest porównywany ze stanem gotowości dla uaktualnienia. Metadane uaktualnienia są pobierane, gdy punkt połączenia z usługą sprawdza dostępność aktualizacji.  

-   **Czas opóźnienia**: Liczba dni, które określają dla **ile dni od opublikowania firmę Microsoft nowego uaktualnienia chcesz czekać przed wdrożeniem w środowisku** w planie obsługi. Program Configuration Manager ocenia, czy dołączać uaktualnienia we wdrożeniu, jeśli bieżąca data jest późniejsza niż data wydania zwiększona o skonfigurowaną liczbę dni.  

 Jeśli uaktualnienie spełnia kryteria, plan obsługi dodaje uaktualnienie do pakietu wdrożeniowego, dystrybuuje pakiet do punktów dystrybucji, a następnie wdraża uaktualnienie w kolekcji na podstawie ustawień skonfigurowanych w planie obsługi.  Wdrożenia można monitorować na kafelku Monitorowanie planu obsługi znajdującym się na pulpicie nawigacyjnym obsługi systemu Windows 10. Aby uzyskać więcej informacji, zobacz [monitorowanie aktualizacji oprogramowania](../../sum/deploy-use/monitor-software-updates.md).  

##  <a name="BKMK_ServicingPlan"></a> Plan obsługi systemu Windows 10  
 Podczas wdrażania systemu Windows 10 CB można utworzyć co najmniej jeden plan obsługi służący do definiowania pierścieni wdrażania w danym środowisku, a następnie monitorować je na pulpicie nawigacyjnym obsługi systemu Windows 10.   
Plany obsługi używają wyłącznie klasyfikacji aktualizacji oprogramowania **Uaktualnienia** , a nie aktualizacji zbiorczych dla systemu Windows 10. W przypadku takich aktualizacji nadal będzie konieczne wdrażanie przy użyciu przepływu pracy aktualizacji oprogramowania.  Środowisko użytkownika końcowego związane z planem obsługi jest takie samo jak w przypadku aktualizacji oprogramowania, włącznie z ustawieniami konfigurowanymi w planie obsługi.  

> [!NOTE]  
>  Można użyć sekwencji zadań w celu wdrożenia uaktualnienia dla każdej kompilacji systemu Windows 10, ale wymaga to więcej czynności ręcznych. Konieczne będzie zaimportowanie zaktualizowanych plików źródłowych jako pakietu uaktualnienia systemu operacyjnego, a następnie utworzenie i wdrożenie sekwencji zadań na odpowiednim zestawie komputerów. Sekwencja zadań zapewnia jednak dodatkowe dostosowywane opcje, takie jak akcje przed wdrożeniem i po wdrożeniu.  

 Podstawowy plan obsługi można utworzyć z poziomu pulpitu nawigacyjnego obsługi systemu Windows 10. Po określeniu nazwy, kolekcji (wyświetlanych jest tylko pierwszych dziesięć kolekcji według rozmiaru, od najmniejszego), pakietu wdrożeniowego (wyświetlanych jest tylko pierwszych dziesięć pakietów w kolejności od ostatnio zmodyfikowanego) i gotowości stanu programu Configuration Manager tworzy plan obsługi z wartościami domyślnymi dla innych ustawień. Można również uruchomić Kreatora tworzenia planu obsługi, aby skonfigurować wszystkie ustawienia. Poniższa procedura umożliwia utworzenie planu obsługi przy użyciu Kreatora tworzenia planu obsługi.  

> [!NOTE]  
>  Począwszy od programu Configuration Manager w wersji 1602, można zarządzać zachowaniem wdrożeń wysokiego ryzyka. Wdrożenie wysokiego ryzyka to wdrożenie, które jest instalowane automatycznie i może mieć niepożądane wyniki. Na przykład sekwencja zadań, której cel to **Wymagane** i która wdraża system Windows 10, jest uznawana za wdrożenie wysokiego ryzyka. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

#### <a name="to-create-a-windows-10-servicing-plan"></a>Aby utworzyć plan obsługi systemu Windows 10  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania rozwiń pozycję **Obsługa systemu Windows 10**, a następnie kliknij pozycję **Plany obsługi**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz plan obsługi**. Zostanie otwarty Kreator tworzenia planu obsługi.  

4.  Na stronie **Ogólne** skonfiguruj następujące ustawienia:  

    -   **Nazwa**: Określ nazwę planu obsługi. Nazwa musi być unikatowa, opisywać cel reguły oraz umożliwiać jej identyfikację spośród innych reguł, w lokacji programu Configuration Manager.  

    -   **Opis elementu**: Określ opis planu obsługi. Opis powinien zawierać omówienie planu obsługi i inne istotne informacje pomocne w identyfikacji i odróżnienia planu między innymi w lokacji programu Configuration Manager. Pole opisu jest opcjonalne, jego limit długości wynosi 256 znaków i jest domyślnie puste.  

5.  Na stronie Plan obsługi skonfiguruj następujące ustawienia:  

    -   **Kolekcja docelowa**: Określa kolekcję docelową używaną dla planu obsługi. Elementy członkowskie kolekcji otrzymują uaktualnienia systemu Windows 10 określone w planie obsługi.  

        > [!NOTE]  
        >  Począwszy od programu Configuration Manager w wersji 1602, wdrażając wysokiego ryzyka, takiego jak wdrożenie planu obsługi, **Wybieranie kolekcji** wyświetlane tylko kolekcje niestandardowe zgodne z ustawieniami weryfikacji wdrożenia skonfigurowanymi we właściwościach lokacji.
        >    
        > Wdrożenia wysokiego ryzyka są zawsze ograniczone do kolekcji niestandardowych, kolekcji tworzonych przez Ciebie i wbudowanej kolekcji **Nieznane komputery** . Podczas tworzeniu wdrożenia wysokiego ryzyka nie można wybrać wbudowanej kolekcji, takiej jak **Wszystkie systemy**. Usuń zaznaczenie pola wyboru **Ukryj kolekcje z elementem członkowskim liczbą większą niż minimalny rozmiar skonfigurowany dla lokacji** Aby wyświetlić wszystkie kolekcje niestandardowe zawierające liczbę klientów niż skonfigurowany maksymalny rozmiar. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >  
        > Ustawienia weryfikacji wdrożenia zależą od bieżącego członkostwa w kolekcji. Po wdrożeniu planu obsługi członkostwo w kolekcji nie jest ponownie oceniane pod kątem ustawień wdrożenia wysokiego ryzyka.  
        >  
        > Na przykład, załóżmy, że ustawisz **domyślny rozmiar** do 100 i **maksymalny rozmiar** do 1000. Podczas tworzenia wdrożenia wysokiego ryzyka w oknie **Wybieranie kolekcji** będą wyświetlane tylko kolekcje zawierające mniej niż 100 klientów. Jeśli wyczyścisz **Ukryj kolekcje z elementem członkowskim liczbą większą niż minimalny rozmiar skonfigurowany dla lokacji** ustawienie, w oknie będą wyświetlane kolekcje zawierające mniej niż 1000 klientów.  
        >
        > W przypadku wybrania kolekcji zawierającej rolę lokacji należy wziąć pod uwagę następujące kwestie:    
        >   
        >    - Jeśli kolekcja zawiera serwer systemu lokacji i skonfigurowano ustawienia weryfikacji wdrożenia w celu blokowania kolekcji z serwerami systemu lokacji, wystąpi błąd i nie będzie można kontynuować.    
        >    - Jeśli kolekcja zawiera serwer systemu lokacji i skonfigurowano ustawienia weryfikacji wdrożenia w celu ostrzegania o kolekcjach zawierających serwery systemu lokacji, to w przypadku przekroczenia domyślnej wartości rozmiaru lub w przypadku kolekcji zawierające serwer w Kreatorze wdrażania oprogramowania zostanie wyświetlone ostrzeżenie o wysokim ryzyku. Musisz zaakceptować utworzenie wdrożenia wysokiego ryzyka. Zostanie utworzony komunikat o stanie inspekcji.  

6.  Na stronie Pierścień wdrażania skonfiguruj następujące ustawienia:  

    -   **Określ stan gotowości systemu Windows, do którego powinien dotyczyć ten plan obsługi**: Wybierz jedną z poniższych opcji:  

        -   **Release Ready (Current Branch)**: W modelu obsługi CB funkcja Aktualizacje są dostępne, jak firma Microsoft udostępnia je.

        -   **Business Ready (Current Branch for Business)**: Gałęzi CBB obsługi jest zwykle używany dla szerokiego wdrożenia. Klienci systemu Windows 10 w CBB obsługi gałęzi odbierać tej samej kompilacji systemu Windows 10, jak w CB obsługi gałęzi, tylko w późniejszym czasie.

        Aby uzyskać więcej informacji o oddziałach obsługi, co opcje najlepiej, zobacz [obsługi gałęzie](https://technet.microsoft.com/itpro/windows/manage/waas-overview#servicing-branches).

    -   **Ile dni od opublikowania przez firmę Microsoft nowego uaktualnienia należy czekać przed wdrożeniem w środowisku**: Program Configuration Manager ocenia, czy dołączać uaktualnienia we wdrożeniu, jeśli bieżąca data jest późniejsza niż data wydania zwiększona liczbę dni, które można skonfigurować dla tego ustawienia.

    -   Przed programu Configuration Manager w wersji 1602, kliknij przycisk **Podgląd** Aby wyświetlić aktualizacje systemu Windows 10 skojarzone z danym stanem gotowości.  

    Aby uzyskać więcej informacji, zobacz [obsługi gałęzie](https://technet.microsoft.com/itpro/windows/manage/waas-overview#servicing-branches).
7.  Począwszy od programu Configuration Manager w wersji 1602, na stronie uaktualnienia Skonfiguruj kryteria wyszukiwania do filtrowania uaktualnień, które zostaną dodane do planu obsługi. Tylko uaktualnienia zgodne z określonymi kryteriami zostaną dodane do skojarzonego wdrożenia.  

     Kliknij pozycję **Podgląd** , aby wyświetlić uaktualnienia spełniające określone kryteria.  

8.  Na stronie Harmonogram wdrażania skonfiguruj następujące ustawienia:  

    -   **Szacowanie harmonogramu**: Określ, czy programu Configuration Manager ma szacować dostępny czas i termin ostateczny instalacji przy użyciu czasu UTC lub czasu lokalnego komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

        > [!NOTE]  
        >  Gdy wybrania czasu lokalnego, a następnie wybierz **jak najszybciej** dla **czas dostępności oprogramowania** lub **ostateczny termin instalacji**czas bieżący na komputerze z systemem konsoli programu Configuration Manager służy do oceny, kiedy aktualizacje są dostępne lub kiedy są instalowane na komputerze klienckim. Jeśli klient znajduje się w innej strefie czasowej, akcje te wystąpią, gdy czas klienta osiągnie czas oceny.  

    -   **Czas dostępności oprogramowania**: Wybierz jedną z następujących ustawień, aby określić, kiedy aktualizacje oprogramowania są dostępne dla klientów:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich tak szybko, jak to możliwe. Po utworzeniu wdrożenia tego ustawienia aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu i będą mogli uzyskać aktualizacje dostępne do zainstalowania.  

        -   **Określony czas**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich w określonym dniu i godzinie. Podczas tworzenia wdrożenia to ustawienie jest włączone, aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu. Aktualizacje oprogramowania we wdrożeniu nie będą jednak dostępne do zainstalowania do skonfigurowanej daty i godziny.  

    -   **Ostateczny termin instalacji**: Wybierz jedną z następujących ustawień, aby określić ostateczny termin instalacji aktualizacji oprogramowania we wdrożeniu:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu najszybciej, jak to możliwe.  

        -   **Określony czas**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu w określonym dniu i godzinie. Configuration Manager określa ostateczny termin instalacji aktualizacji oprogramowania przez dodanie skonfigurowanego **określony czas** interwał **czas dostępności oprogramowania**.  

            > [!NOTE]  
            >  Rzeczywisty ostateczny termin instalacji to wyświetlany czas ostatecznego terminu wydłużony o przypadkowy czas wynoszący maksymalnie 2 godziny. Pozwala to ograniczyć potencjalny wpływ jednoczesnego instalowania aktualizacji we wdrożeniu przez wszystkie komputery klienckie w kolekcji docelowej.  
            >   
            >  Można skonfigurować ustawienie klienta **Agent komputera** , **Wyłącz losowe generowanie terminu ostatecznego** , aby wyłączyć losowe opóźnienie instalacji wymaganych aktualizacji. Aby uzyskać więcej informacji, zobacz sekcję [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent).  

9. Na stronie Czynności użytkownika skonfiguruj następujące ustawienia:  

    -   **Powiadomienia użytkowników**: Określ, czy mają być wyświetlane powiadomienia o aktualizacjach w programie Software Center na komputerze klienckim zgodnie ze skonfigurowanym ustawieniem **czas dostępności oprogramowania** oraz czy wyświetlać powiadomienia użytkowników na komputerach klienckich.  

    -   **Zachowanie ostatecznego terminu wdrożenia**: Określ zachowanie pożądane po osiągnięciu ostatecznego terminu wdrożenia aktualizacji. Określ, czy zainstalować aktualizacje we wdrożeniu. Określ również, czy uruchomić ponownie system po zainstalowaniu aktualizacji niezależnie od skonfigurowanego okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Zachowanie ponownego uruchamiania urządzenia**: Określ, czy pominąć ponowne uruchomienie systemu na serwerach i stacjach roboczych po zainstalowaniu aktualizacji i ponowne uruchomienie systemu jest wymagane do ukończenia instalacji.  

    -   **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: Wdrażając aktualizacje na urządzeniach Windows Embedded z włączoną obsługą filtru zapisu, można określić, aby zainstalować aktualizację na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

        > [!NOTE]  
        >  Przy wdrażaniu aktualizacji na urządzeniu z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi.  

10. Na stronie Pakiet wdrażania wybierz istniejący pakiet wdrożeniowy lub skonfiguruj następujące ustawienia, aby utworzyć nowy pakiet wdrożeniowy:  

    1.  **Nazwa**: Określ nazwę pakietu wdrożeniowego. To musi być unikatowa nazwa opisująca zawartość pakietu. Maksymalna długość to 50 znaków.  

    2.  **Opis elementu**: Określ opis zawierający informacje o pakiecie wdrożeniowym. Długość opisu jest ograniczona do 127 znaków.  

    3.  **Źródło pakietu**: Określa lokalizację plików źródłowych aktualizacji oprogramowania.  Wpisz ścieżkę sieciową do lokalizacji źródłowej, na przykład **\\\serwer\nazwa_udziału\ścieżka**, lub kliknij przycisk **Przeglądaj** , aby znaleźć lokalizację sieciową. Przed kontynuowaniem do następnej strony należy utworzyć folder udostępniony dla plików źródłowych pakietu wdrożeniowego.  

        > [!NOTE]  
        >  Określona lokalizacja źródłowa pakietu wdrożeniowego nie może być używana przez inny pakiet wdrożeniowy oprogramowania.  

        > [!IMPORTANT]  
        >  Zarówno konto komputera dostawcy programu SMS, jak i użytkownik, który uruchamia kreatora w celu pobrania aktualizacji oprogramowania, muszą mieć uprawnienia systemu plików NTFS **Zapis** w lokalizacji pobierania. Aby zapobiec naruszeniu plików źródłowych aktualizacji oprogramowania przez osoby atakujące, należy odpowiednio ograniczyć dostęp do lokalizacji pobierania.  

        > [!IMPORTANT]  
        >  Można zmienić lokalizację źródłową pakietu w oknie właściwości pakietu wdrażania po programu Configuration Manager tworzy pakietu wdrożeniowego. Jednak w celu wykonania tej czynności należy najpierw skopiować zawartość z pierwotnego źródła pakietu do nowej lokalizacji źródłowej pakietu.  

    4.  **Priorytet wysyłania**: Określ priorytet wysyłania pakietu wdrożeniowego. Configuration Manager używa priorytetu wysyłania pakietu wdrożeniowego, gdy wysyła pakiet do punktów dystrybucji. Pakiety wdrożeniowe są wysyłane w kolejności priorytetu: Wysoki, średni lub niski. Pakiety o identycznych priorytetach są wysyłane w kolejności ich utworzenia. Jeżeli nie występuje zaległość, przetwarzanie pakietu rozpocznie się natychmiast niezależnie od jego priorytetu.  

11. Na stronie Punkty dystrybucji określ punkty dystrybucji lub grupy punktów dystrybucji, które będą hostować pliki aktualizacji. Aby uzyskać więcej informacji na temat punktów dystrybucji, zobacz [konfigurowania punktu dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_configs).

    > [!NOTE]  
    >  Ta strona jest dostępna wyłącznie w przypadku utworzenia nowego pakietu wdrożeniowego aktualizacji oprogramowania.  

12. Na stronie Lokalizacja pobierania określ, czy pobierać pliki aktualizacji z Internetu, czy z sieci lokalnej. Skonfiguruj następujące ustawienia:  

    -   **Pobierz aktualizacje oprogramowania z Internetu**: Wybierz to ustawienie, aby pobierać aktualizacje z określonej lokalizacji w Internecie. To ustawienie jest domyślnie włączone.  

    -   **Pobierz aktualizacje oprogramowania z lokalizacji w sieci lokalnej**: Wybierz to ustawienie, aby pobierać aktualizacje z katalogu lokalnego lub folderu udostępnionego. To ustawienie jest przydatne, jeśli komputer, na którym uruchamiasz kreatora, nie ma dostępu do Internetu. Dowolny komputer z dostępem do Internetu może wstępnie pobrać aktualizacje i zapisać je w lokalizacji w sieci lokalnej dostępnej dla komputera, na którym jest uruchamiany kreator.  

13. Na stronie Wybieranie języka wybierz języki, dla których zostaną pobrane wybrane aktualizacje. Aktualizacje zostaną pobrane tylko wtedy, gdy będą dostępne w wybranych językach. Aktualizacje bez określonego języka będą zawsze pobierane. Domyślnie kreator wybierze języki skonfigurowane we właściwościach punktu aktualizacji oprogramowania. Przed przejściem do następnej strony należy wybrać co najmniej jeden język. W przypadku wybrania wyłącznie języków nieobsługiwanych przez aktualizację pobranie aktualizacji zakończy się niepowodzeniem.  

14. Sprawdź ustawienia na stronie Podsumowanie, a następnie kliknij przycisk **Dalej** , aby utworzyć plan obsługi.  

 Plan obsługi zostanie uruchomiony po zakończeniu pracy kreatora. Spowoduje to dodanie aktualizacji spełniających określone kryteria do grupy aktualizacji oprogramowania, pobranie aktualizacji do biblioteki zawartości na serwerze lokacji, rozdystrybuowanie aktualizacji do skonfigurowanych punktów dystrybucji, a następnie wdrożenie grupy aktualizacji oprogramowania na klientach w kolekcji docelowej.  

##  <a name="BKMK_ModifyServicingPlan"></a> Modyfikowanie planu obsługi  
Po utworzeniu podstawowego planu obsługi z poziomu pulpitu nawigacyjnego obsługi systemu Windows 10 lub konieczna zmiana ustawień dla istniejącego planu obsługi, można przejść do właściwości planu obsługi.

> [!NOTE]
> Można skonfigurować ustawienia właściwości planu obsługi, które nie są dostępne w Kreatorze podczas tworzenia planu obsługi. Kreator używa ustawień domyślnych ustawień dla następujących: pobieranie ustawień, ustawienia wdrażania i alerty.  

Aby zmodyfikować właściwości planu obsługi, wykonaj poniższą procedurę.  

#### <a name="to-modify-the-properties-of-a-servicing-plan"></a>Aby zmodyfikować właściwości planu obsługi  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania rozwiń pozycję **Obsługa systemu Windows 10**, kliknij pozycję **Plany obsługi**, a następnie wybierz plan obsługi, który chcesz zmodyfikować.  

3.  Na karcie **Narzędzia główne** kliknij pozycję **Właściwości** , aby otworzyć właściwości wybranego planu obsługi.

    We właściwościach planu obsługi, które nie zostały skonfigurowane w kreatorze dostępne są następujące ustawienia:

    **Ustawienia wdrożenia**: Na karcie Ustawienia wdrożenia skonfiguruj następujące ustawienia:  

    -   **Typ wdrożenia**: Określ typ wdrożenia dla wdrożenia aktualizacji oprogramowania. Wybierz opcję **Wymagane** , aby utworzyć wymagane wdrożenie aktualizacji oprogramowania, w ramach którego aktualizacje oprogramowania zostaną automatycznie zainstalowane na klientach przed upływem skonfigurowanego ostatecznego terminu instalacji. Wybierz opcję **Dostępne** , aby utworzyć opcjonalne wdrożenie aktualizacji oprogramowania, dostępne dla użytkowników do zainstalowania z programu Software Center.  

        > [!IMPORTANT]  
        >  Po utworzeniu wdrożenia aktualizacji oprogramowania nie będzie można zmienić jego typu.  

        > [!NOTE]  
        >  Grupy aktualizacji oprogramowania wdrożone jako **wymagane** zostaną pobrane w tle z uwzględnieniem ustawień usługi BITS, jeśli są skonfigurowane.  
        > Jednak grupy aktualizacji oprogramowania wdrożone jako **dostępne** zostaną pobrane na pierwszym planie, a ustawienia usługi BITS zostaną zignorowane.  

    -   **Użyj funkcji Wake-on-LAN do wzbudzania klientów w celu dokonania wymaganych wdrożeń**: Określ, czy włączyć funkcję Wake On LAN, po upływie terminu wdrożenia, aby wysłać pakiety wznawiania do komputerów wymagających co najmniej jednej aktualizacji oprogramowania we wdrożeniu. Wszelkie komputery w stanie uśpienia w ostatecznym terminie instalacji zostaną wznowione, aby umożliwić zainicjowanie instalacji aktualizacji oprogramowania. Klienci w stanie uśpienia niewymagający aktualizacji oprogramowania w ramach wdrożenia nie zostaną wznowieni. Domyślnie to ustawienie jest wyłączone i jest dostępne wyłącznie po wybraniu opcji **Wymagane** w ustawieniu **Typ wdrożenia**.  

        > [!WARNING]  
        >  Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Poziom szczegółów**: Określ poziom szczegółów komunikatów stanu przesyłanych przez komputery klienckie.  

    **Ustawienia pobierania**: Na karcie Ustawienia pobierania skonfiguruj następujące ustawienia:  

    - Określ, czy klient pobierze i zainstaluje aktualizacje oprogramowania przy użyciu połączenia z powolną siecią lub rezerwowej lokalizacji zawartości.  

    - Określ, czy klient ma pobrać i zainstalować aktualizacje oprogramowania z rezerwowego punktu dystrybucji, jeśli zawartość aktualizacji oprogramowania będzie niedostępna w preferowanym punkcie dystrybucji.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Określ, czy włączyć usługę BranchCache dla pobierania zawartości. Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    -   Określ, czy klienci Pobierz oprogramowanie aktualizacji z witryny Microsoft Update, jeśli aktualizacje oprogramowania nie są dostępne w punktach dystrybucji.
        > [!IMPORTANT]
        > Nie używaj tego ustawienia aktualizacje obsługi systemu Windows 10. Configuration Manager (co najmniej do wersji 1610) zakończy się niepowodzeniem pobrać aktualizacje obsługi systemu Windows 10 z witryny Microsoft Update.

    -   Określ, czy zezwolić klientom używającym taryfowego połączenia z Internetem na pobieranie aktualizacji oprogramowania po upływie ostatecznego terminu instalacji. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.   

    **Alerty**: Na karcie alerty Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager. Alerty można skonfigurować wyłącznie po wybraniu opcji **Wymagane** ustawienia **Typ wdrożenia** na stronie Ustawienia wdrożenia.  

    > [!NOTE]  
    >  Ostatnie alerty dotyczące aktualizacji oprogramowania można wyświetlić w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  
