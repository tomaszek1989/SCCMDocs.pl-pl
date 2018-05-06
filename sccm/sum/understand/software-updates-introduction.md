---
title: Wprowadzenie do aktualizacji oprogramowania
titleSuffix: Configuration Manager
description: Poznaj podstawy aktualizacji oprogramowania w programie System Center Configuration Manager.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 10/30/2017
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: e9778b13-c8a3-40eb-8655-34ac8ce9cdaa
ms.openlocfilehash: d5528fc3e035cd5bed8bc92c8b65f3025d97a2d1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-software-updates-in-system-center-configuration-manager"></a>Wprowadzenie do aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aktualizacje oprogramowania w programie System Center Configuration Manager udostępnia zestaw narzędzi i zasobów, które ułatwiają zarządzanie złożonymi zadaniami śledzenia i stosowania aktualizacji oprogramowania na komputerach klienckich w przedsiębiorstwie. Efektywny proces zarządzania aktualizacjami oprogramowania jest konieczny do zachowania skuteczności działania, rozwiązywania problemów dotyczących zabezpieczeń i zachowania stabilności infrastruktury sieciowej. Jednakże z powodu zmienności technologii i stałego pojawiania się nowych zagrożeń bezpieczeństwa efektywne zarządzanie aktualizacjami oprogramowania wymaga stałej uwagi.  

Przykładowy scenariusz przedstawiający sposób demonstrujący wdrażanie aktualizacji oprogramowania w danym środowisku, zobacz [przykładowy scenariusz wdrażania aktualizacji oprogramowania zabezpieczającego](../deploy-use/example-scenario-deploy-monitor-monthly-security-updates.md).  

##  <a name="BKMK_Synchronization"></a> Synchronizacja aktualizacji oprogramowania  
 Synchronizacja aktualizacji oprogramowania w programie Configuration Manager łączy się z witryną Microsoft Update do pobierania metadanych aktualizacji oprogramowania. Lokacji najwyższego poziomu (centralna lokacja administracyjna lub autonomiczna lokacja główna) synchronizuje się z usługą Microsoft Update zgodnie z harmonogramem lub po ręcznym rozpoczęciu synchronizacji z konsoli programu Configuration Manager. Po zakończeniu synchronizacji aktualizacji oprogramowania w lokacji najwyższego poziomu programu Configuration Manager w lokacjach podrzędnych, rozpoczyna się synchronizacja aktualizacji oprogramowania, jeżeli istnieją. Po ukończeniu synchronizacji w każdej lokacji dodatkowej lub głównej tworzone są zasady dla całej lokacji udostępniające komputerom klienckim lokalizację punktów aktualizacji oprogramowania.  

> [!NOTE]  
>  Aktualizacje oprogramowania są domyślnie włączone w ustawieniach klienta. Jednakże w przypadku wybrania dla ustawienia klienta **Włącz aktualizacje oprogramowania na klientach** wartości **Nie** w celu wyłączenia aktualizacji oprogramowania w kolekcji lub w ustawieniach domyślnych, lokalizacja punktów aktualizacji oprogramowania nie jest wysyłana do skojarzonych klientów. Aby uzyskać więcej informacji, zobacz [ustawienia klienta aktualizacji oprogramowania](../../core/clients/deploy/about-client-settings.md#software-updates).  

 Po odebraniu zasad klient rozpocznie skanowanie pod kątem zgodności aktualizacji oprogramowania i zapisze informacje w Instrumentacji zarządzania Windows (WMI). Informacje o zgodności są następnie wysyłane do punktu zarządzania, który wysyła je serwera lokacji. Więcej informacji na temat oceny zgodności zawiera sekcja [Software updates compliance assessment](#BKMK_SUMCompliance) w tym temacie.  

 W lokacji głównej można instalować wiele punktów aktualizacji oprogramowania. Pierwszy zainstalowany punkt aktualizacji oprogramowania jest konfigurowany jako źródło synchronizacji. Służy do synchronizacji z usługi Microsoft Update lub serwer WSUS spoza hierarchii programu Configuration Manager. Inne punkty aktualizacji oprogramowania w lokacji używają jako źródła synchronizacji pierwszego punktu aktualizacji oprogramowania.  

> [!NOTE]  
>  Po ukończeniu procesu synchronizacji aktualizacji oprogramowania w lokacji najwyższego poziomu metadane aktualizacji oprogramowania są replikowane w lokacjach podrzędnych za pomocą replikacji bazy danych. Po podłączeniu konsoli programu Configuration Manager do lokacji podrzędnej programu Configuration Manager Wyświetla metadane aktualizacji oprogramowania. Jednak do momentu zainstalowania i skonfigurowania punktu aktualizacji oprogramowania w lokacji, klienci nie będą skanować pod kątem zgodności aktualizacji oprogramowania, klienci nie będą zgłaszać informacji o zgodności do programu Configuration Manager i nie można pomyślnie wdrożyć aktualizacji oprogramowania.  

### <a name="synchronization-on-the-top-level-site"></a>Synchronizacja w lokacji najwyższego poziomu  
 Proces synchronizacji aktualizacji oprogramowania w lokacji najwyższego poziomu powoduje pobranie z usługi Microsoft Update metadanych aktualizacji oprogramowania spełniających kryteria określone we właściwościach Składnika punktu aktualizacji oprogramowania. Kryteria należy skonfigurować tylko w lokacji najwyższego poziomu.  

> [!NOTE]  
>  Można określić istniejący serwer WSUS, który nie znajduje się w hierarchii programu Configuration Manager, zamiast Microsoft Updates jako źródło synchronizacji.  

 Poniższa lista zawiera opis podstawowych kroków procesu synchronizacji w lokacji najwyższego poziomu:  

1.  Rozpoczyna się synchronizacja aktualizacji oprogramowania.  

2.  Menedżer synchronizacji programu WSUS wysyła do usługi WSUS działającej w punkcie aktualizacji oprogramowania żądanie rozpoczęcia synchronizacji z usługą Microsoft Update.  

3.  Metadane aktualizacji oprogramowania są synchronizowane z usługą Microsoft Update, a wszelkie zmiany są wstawiane i aktualizowane w bazie danych usługi WSUS.  

4.  Po zakończeniu synchronizacji programu WSUS Menedżer synchronizacji programu WSUS Synchronizuje metadane aktualizacji oprogramowania z bazy danych programu WSUS w bazie danych programu Configuration Manager, a wszelkie zmiany od ostatniej synchronizacji są wstawiane lub aktualizowane w bazie danych lokacji. Metadane aktualizacji oprogramowania są przechowywane w bazie danych lokacji jako element konfiguracji.  

5.  Elementy konfiguracji aktualizacji oprogramowania są wysyłane do lokacji podrzędnych za pomocą replikacji bazy danych.  

6.  Po pomyślnym zakończeniu synchronizacji Menedżer synchronizacji programu WSUS tworzy komunikat o stanie 6702.  

7.  Menedżer synchronizacji programu WSUS wysyła żądanie synchronizacji do wszystkich lokacji podrzędnych.  

8.  Menedżer synchronizacji programu WSUS wysyła pojedynczo żądania do usługi WSUS działającej w innych punktach aktualizacji oprogramowania w lokacji. Serwery programu WSUS w innych punktach aktualizacji oprogramowania są skonfigurowane jako repliki usługi WSUS działające w domyślnym punkcje aktualizacji oprogramowania w lokacji.  

### <a name="synchronization-on-child-primary-and-secondary-sites"></a>Synchronizacja w głównych i dodatkowych lokacjach podrzędnych  
 Podczas procesu synchronizacji aktualizacji oprogramowania w lokacji najwyższego poziomu elementy konfiguracji aktualizacji oprogramowania są replikowane w lokacjach podrzędnych za pomocą replikacji bazy danych. Po zakończeniu procesu lokacja najwyższego poziomu wysyła żądanie synchronizacji do lokacji podrzędnej, a lokacja podrzędna rozpoczyna synchronizację z programem WSUS. Poniższa lista zawiera podstawowe kroki procesu synchronizacji w głównej i dodatkowej lokacji podrzędnej:  

1.  Menedżer synchronizacji programu WSUS odbiera żądanie synchronizacji z lokacji najwyższego poziomu.  

2.  Rozpoczyna się synchronizacja aktualizacji oprogramowania.  

3.  Menedżer synchronizacji programu WSUS żąda rozpoczęcia synchronizacji od usługi WSUS działającej w punkcie aktualizacji oprogramowania.  

4.  Usługa WSUS działająca w punkcie aktualizacji oprogramowania w lokacji podrzędnej synchronizuje metadane aktualizacji oprogramowania z usługą WSUS działającą w punkcje aktualizacji oprogramowania w lokacji nadrzędnej.  

5.  Po pomyślnym zakończeniu synchronizacji Menedżer synchronizacji programu WSUS tworzy komunikat o stanie 6702.  

6.  Menedżer synchronizacji programu WSUS wysyła żądanie synchronizacji do wszystkich podrzędnych lokacji dodatkowych. Lokacja podrzędna rozpoczyna synchronizację aktualizacji oprogramowania z nadrzędną lokacją główną. Lokacja dodatkowa jest konfigurowana jako replika usługi WSUS działającej w lokacji nadrzędnej.  

7.  Menedżer synchronizacji programu WSUS wysyła pojedynczo żądania do usługi WSUS działającej w innych punktach aktualizacji oprogramowania w lokacji. Serwery programu WSUS w innych punktach aktualizacji oprogramowania są skonfigurowane jako repliki usługi WSUS działające w domyślnym punkcje aktualizacji oprogramowania w lokacji.  

##  <a name="BKMK_SUMCompliance"></a> Software updates compliance assessment  
 Przed wdrożeniem aktualizacji oprogramowania na komputerach klienckich w programie Configuration Manager, należy rozpocząć skanowanie pod kątem zgodności aktualizacji oprogramowania na komputerach klienckich. Dla każdej aktualizacji oprogramowania zostanie utworzony komunikat o stanie zawierający stan zgodności aktualizacji. Komunikaty o stanie są wysyłane w trybie zbiorczym do punktu zarządzania, a następnie do serwera lokacji, gdzie stan zgodności jest wstawiany do bazy danych lokacji. Stan zgodności aktualizacji oprogramowania jest wyświetlany w konsoli programu Configuration Manager. Aktualizacje oprogramowania można wdrożyć i zainstalować na komputerach, które wymagają aktualizacji. Poniższe sekcje zawierają informacje o stanach zgodności i opis procesu skanowania pod kątem zgodności aktualizacji oprogramowania.  

### <a name="software-updates-compliance-states"></a>Stany zgodności aktualizacji oprogramowania  
 Poniżej wymieniono i opisano każdy stan zgodności jest wyświetlana w konsoli programu Configuration Manager dla aktualizacji oprogramowania.  

-   **Wymagane**  

     Oznacza, że aktualizacja oprogramowania ma zastosowanie i jest wymagana na komputerze klienckim. Poniższe warunki mogą być spełnione, gdy stan aktualizacji oprogramowania to **Wymagane**:  

    -   Aktualizacja oprogramowania nie została wdrożona na komputerze klienckim.  

    -   Aktualizacja oprogramowania została zainstalowana na komputerze klienckim. Jednakże najnowszy komunikat o stanie nie został jeszcze wstawiony do bazy danych na serwerze lokacji. Komputer kliencki ponownie skanuje pod kątem dostępności aktualizacji po zakończeniu instalacji. Klient może wysłać zaktualizowany stan do punktu zarządzania, a następnie przekazać zaktualizowany stan do serwera lokacji z około dwuminutowym opóźnieniem.  

    -   Aktualizacja oprogramowania została zainstalowana na komputerze klienckim. Jednakże instalacja aktualizacji oprogramowania wymaga ponownego uruchomienia komputera przed ukończeniem aktualizacji.  

    -   Aktualizacja oprogramowania została wdrożona na komputerze klienckim, ale nie została jeszcze zainstalowana.  

-   **Niewymagane**  

     Oznacza, że aktualizacja oprogramowania nie ma zastosowania na komputerze klienckim. Dlatego aktualizacja oprogramowania nie jest wymagana.  

-   **Zainstalowane**  

     Oznacza, że aktualizacja oprogramowania ma zastosowanie na komputerze klienckim i została już na nim zainstalowana.  

-   **Nieznane**  

     Oznacza, że serwer lokacji nie odebrał komunikatu o stanie z komputera klienckiego z jednego z następujących powodów:  

    -   Komputer kliencki nie wykonał pomyślnie skanowania pod kątem zgodności aktualizacji oprogramowania.  

    -   Skanowanie na komputerze klienckim zakończyło się pomyślnie. Jednakże komunikat o stanie nie został jeszcze przetworzony na serwerze lokacji, prawdopodobnie z powodu zaległości komunikatu o stanie.  

    -   Skanowanie na komputerze klienckim zakończyło się pomyślnie, ale komunikat o stanie nie został odebrany z witryny podrzędnej.  

    -   Skanowanie na komputerze klienckim zakończyło się pomyślnie, ale plik komunikatu o stanie został uszkodzony i nie można było go przetworzyć.  

### <a name="scan-for-software-updates-compliance-process"></a>Proces skanowania pod kątem zgodności z aktualizacjami oprogramowania  
 Po zainstalowaniu i zsynchronizowaniu punktu aktualizacji oprogramowania tworzone są zasady dla całej lokacji, które informują komputery klienckie, że aktualizacje oprogramowania Configuration Manager zostało włączone dla tej lokacji. Gdy klient odbierze zasady komputera, planowane jest losowe rozpoczęcie skanowania oceny zgodności w ciągu następnych dwóch godzin. Po rozpoczęciu skanowania proces Agent klienta aktualizacji oprogramowania czyści historię skanowania, przesyła żądanie znalezienia serwera WSUS, który ma zostać użyty do skanowania i aktualizuje lokalizację serwera WSUS w zasadach grupy.  

> [!NOTE]  
>  Klienci internetowi muszą połączyć się z serwerem WSUS, używając protokołu SSL.  

 Żądanie skanowania zostaje przekazane do usługi Windows Update Agent (WUA). Usługa WUA łączy się następnie z lokalizacją serwera usług WSUS wskazaną w zasadzie lokalnej, pobiera metadane aktualizacji oprogramowania, które zostały zsynchronizowane na serwerze WSUS, i skanuje komputer kliencki pod kątem aktualizacji. Proces agenta klienta aktualizacji oprogramowania (Software Updates Client Agent) wykrywa, że skanowanie pod kątem zgodności zakończyło się, i tworzy komunikaty o stanie dla każdej aktualizacji oprogramowania, która zmieniła swój stan zgodności od ostatniego skanowania. Komunikaty o stanie są wysyłane do punktu zarządzania zbiorczo co 15 minut. Punkt zarządzania przesyła następnie komunikaty o stanie do serwera lokacji, w którym są one wstawiane do bazy danych serwera lokacji.  

 Po wstępnym skanowaniu pod kątem zgodności z aktualizacjami oprogramowania skanowanie jest uruchamiane zgodnie ze skonfigurowanym harmonogramem skanowania. Jeśli jednak klient wykonał skanowanie pod kątem zgodności aktualizacji oprogramowania w ramach czasowych wskazanych przez wartość czasu wygaśnięcia (Time to Live, TTL), klient korzysta z metadanych aktualizacji oprogramowania, które są przechowywane lokalnie. Kiedy ostatnie skanowanie przypada poza czasem wygaśnięcia, klient musi połączyć się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania i zaktualizować metadane aktualizacji oprogramowania przechowywane na kliencie.  

 Skanowanie pod kątem zgodności z aktualizacjami oprogramowania można uruchamiać następującymi metodami, wliczając w to harmonogram skanowania:  

-   **Harmonogram skanowania w poszukiwaniu aktualizacji oprogramowania**: Skanowanie pod kątem oprogramowania zgodności z aktualizacjami uruchamiane zgodnie z harmonogramem skanowania, skonfigurowanym w ustawieniach agenta klienta aktualizacji oprogramowania. Aby uzyskać więcej informacji o sposobie konfigurowania ustawień klienta aktualizacji oprogramowania, zobacz [ustawienia klienta aktualizacji oprogramowania](../../core/clients/deploy/about-client-settings.md#software-updates).  

-   **Działanie właściwości programu Configuration Manager**: Użytkownik może uruchomić **cykl skanowania aktualizacji oprogramowania** lub **cykl oceny wdrożenia aktualizacji oprogramowania** akcji **akcji** karcie **właściwości programu Configuration Manager** okno dialogowe na komputerze klienckim.  

-   **Harmonogram ponownej oceny wdrożenia**: Ocena wdrożenia i skanowanie w poszukiwaniu oprogramowania zgodności z aktualizacjami uruchamiane zgodnie z harmonogramem ponownej oceny skonfigurowanego wdrożenia, który jest skonfigurowany w ustawieniach agenta klienta aktualizacji oprogramowania. Aby uzyskać więcej informacji o ustawieniach klienta aktualizacji oprogramowania, zobacz [ustawienia klienta aktualizacji oprogramowania](../../core/clients/deploy/about-client-settings.md#software-updates).  

-   **Przed pobraniem plików aktualizacji**: Kiedy komputer klienta otrzymuje zasady przypisywania dotyczące nowo wymaganego wdrożenia, Agent klienta aktualizacji oprogramowania pobiera pliki aktualizacji oprogramowania do lokalnej pamięci podręcznej klienta. Przed pobraniem plików aktualizacji oprogramowania agent klienta uruchamia skanowanie, aby zweryfikować, że aktualizacja oprogramowania jest nadal wymagana.  

-   **Przed zainstalowaniem aktualizacji oprogramowania**: Tuż przed instalacją aktualizacji oprogramowania Agent klienta aktualizacji oprogramowania uruchamia skanowanie, aby zweryfikować, czy aktualizacje oprogramowania są nadal wymagane.  

-   **Po zainstalowaniu aktualizacji oprogramowania**: Tuż po ukończeniu instalacji aktualizacji oprogramowania Agent klienta aktualizacji oprogramowania uruchamia skanowanie, aby zweryfikować, że aktualizacje oprogramowania nie są już wymagane i tworzy nowy komunikat o stanie stwierdzający, że aktualizacja oprogramowania została zainstalowana. Kiedy instalacja zakończyła się, ale wymaga ponownego uruchomienia, komunikat o stanie wskazuje, że komputer klienta oczekuje na ponowne uruchomienie.  

-   **Po ponownym uruchomieniu systemu**: Gdy komputer kliencki oczekuje na ponowne uruchomienie systemu, aby ukończyć instalację aktualizacji oprogramowania, Agent klienta aktualizacji oprogramowania uruchamia skanowanie po ponownym uruchomieniu, aby sprawdzić, czy aktualizacja oprogramowania nie jest już wymagane i tworzy komunikat o stanie stwierdzający, że aktualizacja oprogramowania została zainstalowana.  

#### <a name="time-to-live-value"></a>Wartość czasu wygaśnięcia  
 Metadane aktualizacji oprogramowania wymagane do skanowania pod kątem zgodności z aktualizacjami oprogramowania są magazynowane na lokalnym komputerze klienta i domyślnie ważne przez najwyżej 24 godziny. Ta wartość jest znana jako czas wygaśnięcia.  

#### <a name="scan-for-software-updates-compliance-types"></a>Typy skanowania pod kątem zgodności z aktualizacjami oprogramowania  
 Przeprowadzając skanowanie pod kątem zgodności z aktualizacjami oprogramowania, klient korzysta ze skanowania w trybie online lub offline i wymuszonym lub niewymuszonym, zależnie od sposobu uruchomienia skanowania pod kątem zgodności z aktualizacjami oprogramowania. Poniżej opisano, które metody uruchamiania skanowania działają w trybie online w trybie offline, a także czy skanowanie jest wymuszone, czy niewymuszone.  

-   **Harmonogram skanowania w poszukiwaniu aktualizacji oprogramowania** (niewymuszone skanowanie w trybie online)  

     Zgodnie ze skonfigurowanym harmonogramem skanowania klient łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania tylko wtedy, gdy ostatnie skanowanie przypadło poza czasem wygaśnięcia.  

-   **Cykl skanowania aktualizacji oprogramowania** lub **cykl oceny wdrożenia aktualizacji oprogramowania** (wymuszone skanowanie w trybie online)  

     Komputer klienta zawsze łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania, zanim przeprowadzi skanowanie pod kątem zgodności z aktualizacjami oprogramowania. Po ukończeniu skanowania licznik czasu wygaśnięcia zostaje zresetowany. Jeśli na przykład czas wygaśnięcia wynosi 24 godziny, to po uruchomieniu przez użytkownika skanowania pod kątem zgodności z aktualizacjami oprogramowania czas wygaśnięcia zostaje zresetowany do 24 godzin.  

-   **Harmonogram ponownej oceny wdrożenia** (niewymuszone skanowanie w trybie online)  

     Zgodnie ze skonfigurowanym harmonogramem ponownej oceny wdrożenia klient łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania tylko wtedy, gdy ostatnie skanowanie przypadło poza czasem wygaśnięcia.  

-   **Przed pobraniem plików aktualizacji** (niewymuszone skanowanie w trybie online)  

     Aby móc pobrać pliki aktualizacji w wymaganych wdrożeniach, klient łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania tylko wtedy, gdy ostatnie skanowanie przypadło poza czasem wygaśnięcia.  

-   **Przed zainstalowaniem aktualizacji oprogramowania** (niewymuszone skanowanie w trybie online)  

     Aby móc zainstalować aktualizacje oprogramowania w wymaganych wdrożeniach, klient łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania tylko wtedy, gdy ostatnie skanowanie przypadło poza czasem wygaśnięcia.  

-   **Po zainstalowaniu aktualizacji oprogramowania** (wymuszone skanowanie w trybie offline)  

     Po zainstalowaniu aktualizacji oprogramowania agent klienta aktualizacji oprogramowania uruchamia skanowanie, posługując się metadanymi lokalnymi. Klient nie łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania.  

-   **Po ponownym uruchomieniu systemu** (wymuszone skanowanie w trybie offline)  

     Po zainstalowaniu aktualizacji oprogramowania i ponownym uruchomieniu komputera agent klienta aktualizacji oprogramowania uruchamia skanowanie, posługując się metadanymi lokalnymi. Klient nie łączy się z usługami WSUS działającymi w punkcie aktualizacji oprogramowania, aby pobrać metadane aktualizacji oprogramowania.  

##  <a name="BKMK_DeploymentPackages"></a> Pakiety wdrożeniowe aktualizacji oprogramowania  
 Pakiet wdrożeniowy aktualizacji oprogramowania to mechanizm służący do pobierania aktualizacji oprogramowania do udostępnionego folderu sieciowego oraz kopiowania plików źródłowych aktualizacji oprogramowania do biblioteki zawartości na serwerach lokacji i w punktach dystrybucji zdefiniowanych we wdrożeniu. Korzystając z kreatora pobierania aktualizacji, można pobierać aktualizacje oprogramowania i dodawać je do pakietów wdrożeniowych przed ich wdrożeniem. Ten kreator pozwala udostępniać aktualizacje oprogramowania w punktach dystrybucji i weryfikować, że ta część procesu wdrażania zakończyła się powodzeniem, przed przystąpieniem do wdrażania aktualizacji oprogramowania na klientach.  

 Podczas wdrażania pobranych aktualizacji oprogramowania za pomocą kreatora wdrażania aktualizacji oprogramowania wdrożenie automatycznie wykorzystuje pakiet wdrożeniowy zawierający aktualizacje oprogramowania. W przypadku wdrażania aktualizacji oprogramowania, które nie zostały pobrane, należy określić w kreatorze wdrażania aktualizacji oprogramowania nowy lub istniejący pakiet wdrożeniowy i aktualizacje oprogramowania zostaną pobrane po zakończeniu działania kreatora.  

> [!IMPORTANT]  
>  Przed określeniem w kreatorze udostępnionego folderu sieciowego dla plików źródłowych pakietu wdrożeniowego należy ręcznie utworzyć ten folder. Każdy pakiet wdrożeniowy musi korzystać z innego udostępnionego folderu sieciowego.  

> [!IMPORTANT]  
>  Zarówno konto komputera dostawcy programu SMS, jak i użytkownik administracyjny, który pobiera aktualizacje oprogramowania, muszą mieć uprawnienia **Zapis** do źródła pakietu. Aby zmniejszyć ryzyko naruszenia przez osoby atakujące plików źródłowych aktualizacji oprogramowania znajdujących się w źródle pakietu, należy odpowiednio ograniczyć dostęp do źródła pakietu.  

 Podczas tworzenia nowego pakietu wdrożeniowego numer wersji zawartości zostaje ustawiony na 1 jeszcze przed pobraniem jakichkolwiek aktualizacji oprogramowania. Kiedy za pomocą pakietu zostają pobrane pliki aktualizacji oprogramowania, numer wersji zawartości zwiększa się do 2. Dlatego też wszystkie nowe pakiety wdrożeniowe uruchamiają się z wersją zawartości zaczynającą się od 2. Za każdym razem, kiedy zawartość pakietu wdrożeniowego ulega zmianie, numer wersji zawartości zwiększa się o 1. Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

 Klienci instalują aktualizacje oprogramowania we wdrożeniu, korzystając z dowolnego punktu dystrybucji mającego dostępne aktualizacje oprogramowania, niezależnie od pakietu wdrożeniowego. Nawet jeśli któryś z pakietów wdrożeniowych dla aktywnego wdrożenia zostanie usunięty, klienci nadal mogą zainstalować aktualizacje oprogramowania we wdrożeniu, o ile tylko każda z aktualizacji została pobrana do co najmniej jednego innego pakietu wdrożeniowego i jest dostępna w punkcie dystrybucji, do którego ma dostęp dany klient. Wraz z usunięciem ostatniego pakietu wdrożeniowego zawierającego aktualizację oprogramowania komputery klienckie tracą możliwość pobrania aktualizacji oprogramowania, dopóki aktualizacja nie zostanie ponownie pobrana do pakietu wdrożeniowego. Aktualizacje oprogramowania są wyświetlane z czerwoną strzałką w konsoli programu Configuration Manager, jeśli pliki aktualizacji nie są w żadnym pakiecie wdrożeniowym. Wdrożenia, które zawierają jakiekolwiek aktualizacje w tym stanie, są wyświetlane z podwójną czerwoną strzałką.  

##  <a name="BKMK_DeploymentWorkflows"></a> Przepływy pracy wdrożeń aktualizacji oprogramowania  
 Istnieją dwa główne scenariusze wdrażania aktualizacji oprogramowania w danym środowisku: wdrażanie ręczne i wdrażanie automatyczne. Zazwyczaj wdrażania aktualizacji oprogramowania ręcznie, aby utworzyć linię bazową dla klienta na komputery, a następnie zarządzanie aktualizacjami oprogramowania na klientach za pomocą wdrażania automatycznego. W poniższych częściach omówiono przepływ pracy ręcznego i automatycznego wdrażania aktualizacji oprogramowania.  

###  <a name="BKMK_ManualDeployment"></a> Ręczne wdrażanie aktualizacji oprogramowania  
 Ręczne wdrażanie aktualizacji oprogramowania to proces wyborze aktualizacji oprogramowania w konsoli programu Configuration Manager i ręcznym uruchomieniu procedury wdrażania. Tę metodę wdrażania stosuje się najczęściej po to, aby uaktualnić komputery klienckie za pomocą wymaganych aktualizacji oprogramowania przed utworzeniem zasad wdrażania automatycznego, zarządzających ciągłymi comiesięcznymi wdrożeniami aktualizacji oprogramowania, i aby wdrożyć wymagania aktualizacji oprogramowania poza pasmem. Na poniższej liście przedstawiono ogólny przepływ pracy ręcznego wdrażania aktualizacji oprogramowania:  

1.  Odfiltrowanie aktualizacji oprogramowania, które korzystają z określonych wymagań. Można na przykład podać kryteria pozwalające pobrać wszystkie aktualizacje oprogramowania zabezpieczeń lub krytyczne aktualizacje oprogramowania, jakie są wymagane na ponad 50 komputerach klienckich.  

2.  Tworzenie grupy aktualizacji oprogramowania, zawierającej aktualizacje oprogramowania.  

3.  Pobranie zawartości dla aktualizacji oprogramowania należących do grupy aktualizacji oprogramowania.  

4.  Ręczne wdrożenie grupy aktualizacji oprogramowania.  

###  <a name="BKMK_AutomaticDeployment"></a> Automatyczne wdrażanie aktualizacji oprogramowania  
 Automatyczne wdrażanie aktualizacji oprogramowania konfiguruje się za pomocą reguły wdrażania automatycznego (ADR). Tę metodę wdrażania stosuje się najczęściej do comiesięcznych aktualizacji oprogramowania (znanych jako „wtorek poprawek”) i do zarządzania aktualizacjami definicji. Po uruchomieniu reguły aktualizacje oprogramowania są usuwane z grupy aktualizacji oprogramowania (jeśli jest używana istniejąca grupa) i aktualizacje oprogramowania spełniające określone kryteria (na przykład wszystkie aktualizacje zabezpieczeń oprogramowania) są dodawane do grupy aktualizacji oprogramowania. Następnie pliki zawartości aktualizacji oprogramowania są pobierane i kopiowane do punktów dystrybucji, a aktualizacje oprogramowania są wdrażane na komputerach klienckich w docelowej kolekcji. Na poniższej liście przedstawiono ogólny przepływ pracy automatycznego wdrażania aktualizacji oprogramowania:  

1.  Utwórz regułę ADR określającą ustawienia wdrożenia, takie jak:  

    -   Kolekcja docelowa  

    -   Zdecyduj, czy dla komputerów klienckich w kolekcji docelowej włączyć wdrażanie, czy raportowanie o zgodności z aktualizacjami oprogramowania  

    -   Kryteria aktualizacji oprogramowania  

    -   Harmonogramy oceny i wdrożenia  

    -   Środowisko użytkownika  

    -   Właściwości pobierania  

2.  Aktualizacje oprogramowania zostają dodane do grupy aktualizacji oprogramowania.  

3.  Grupa aktualizacji oprogramowania jest wdrażana na komputerach klienckich w kolekcji docelowej, jeśli została określona.  

 Należy ustalić, jaką strategię wdrażania zastosować w danym środowisku. Można na przykład utworzyć regułę ADR, obierając za cel kolekcję klientów testowych. Po zweryfikowaniu, że aktualizacje oprogramowania zostały zainstalowane w tej grupie testowej, można dodać nowe wdrożenie do reguły lub zmienić kolekcję w istniejącym wdrożeniu na kolekcję docelową obejmującą większy zestaw klientów. Obiekty aktualizacji oprogramowania tworzone przez reguły ADR są interaktywne.  

-   Aktualizacje oprogramowania wdrożone za pomocą reguły ADR są automatycznie wdrażane na nowych klientach dodawanych do kolekcji docelowej.  

-   Nowe aktualizacje oprogramowania dodawane do grupy aktualizacji oprogramowania są automatycznie wdrażane na klientach w kolekcji docelowej.  

-   Wdrożenia na użytek reguły ADR można w każdej chwili włączać lub wyłączać.  

 Po utworzeniu reguły ADR można dodać do niej dodatkowe wdrożenia. Dzięki temu można uprościć wdrażanie różnych aktualizacji w różnych kolekcjach. Dla każdego nowego wdrożenia dostępny jest pełny zakres funkcji wraz z możliwością monitorowania wdrożenia, a każde nowe dodane wdrożenie:  

-   Używa tej samej grupy aktualizacji i tego samego pakietu utworzonego przy pierwszym uruchomieniu reguły wdrażania automatycznego.  

-   Możliwość określenia innej kolekcji.  

-   Obsługa unikatowych właściwości wdrożenia, w tym poniższych:  

    -   Czas aktywacji  

    -   Termin  

    -   Włączenie lub wyłączenie czynności użytkownika  

    -   Oddzielne alerty dla wdrożenia  

##  <a name="BKMK_DeploymentProcess"></a> Proces wdrażania aktualizacji oprogramowania  
 Po wdrożeniu aktualizacji oprogramowania lub po uruchomieniu zasady wdrażania automatycznego, która wdraża aktualizacje oprogramowania, do zasad komputera dla danej lokacji zostają dodane zasady przypisywania wdrożenia. Aktualizacje oprogramowania zostają pobrane z lokalizacji pobierania, Internetu lub udostępnionego folderu sieciowego do źródła pakietu. Aktualizacje oprogramowania zostają skopiowane ze źródła pakietu do biblioteki zawartości na serwerze lokacji, a następnie do biblioteki zawartości w punkcie dystrybucji.  

 Gdy komputer kliencki w kolekcji docelowej wdrożenia otrzyma zasady komputera, agent klienta aktualizacji oprogramowania rozpocznie skanowanie w celu przeprowadzenia oceny. Agent klienta pobierze zawartość wymaganych aktualizacji oprogramowania z dystrybucji wskaż pamięci podręcznej na **czas dostępności oprogramowania** ustawienie dla wdrożenia, a następnie oprogramowania aktualizacje są dostępne do zainstalowania . Aktualizacje oprogramowania we wdrożeniach opcjonalnych (bez ostatecznego terminu instalacji) nie zostaną pobrane do momentu ręcznego rozpoczęcia instalacji przez użytkownika.  

 Po upływie skonfigurowanego terminu ostatecznego agent klienta aktualizacji oprogramowania przeprowadzi skanowanie w celu sprawdzenia, czy aktualizacje oprogramowania są nadal wymagane. Następnie sprawdzi lokalną pamięć podręczną na komputerze klienckim, aby potwierdzić, czy pliki źródłowe aktualizacji oprogramowania są wciąż dostępne. Następnie zainstaluje aktualizacje oprogramowania. Jeśli usunięto zawartość z pamięci podręcznej klienta, aby pomieścić inne wdrożenie, aktualizacje oprogramowania zostaną pobrane ponownie z punktu dystrybucji do pamięci podręcznej klienta. Aktualizacje oprogramowania są zawsze pobierane do pamięci podręcznej klienta, niezależnie od jej skonfigurowanego maksymalnego rozmiaru. Po ukończeniu instalacji agent klienta sprawdzi, czy aktualizacje oprogramowania są nadal wymagane, a następnie prześle komunikat o stanie do punktu zarządzania w celu potwierdzenia, że aktualizacje oprogramowania zostały zainstalowane na kliencie.  

### <a name="required-system-restart"></a>Wymagane ponowne uruchomienie systemu  
 Jeśli po zainstalowaniu aktualizacji oprogramowania z wymaganego wdrożenia na komputerze klienckim ukończenie instalacji będzie wymagało ponownego uruchomienia, zgodnie z domyślnym ustawieniem system zostanie uruchomiony ponownie. W przypadku aktualizacji oprogramowania zainstalowanych przed terminem ostatecznym automatyczne ponowne uruchomienie systemu zostanie wstrzymane do czasu terminu ostatecznego, jeśli komputer nie zostanie uruchomiony ponownie wcześniej z innej przyczyny. Ponowne uruchomienie systemu można pominąć na serwerach i stacjach roboczych. Te ustawienia można skonfigurować na stronie **Czynności użytkownika** Kreatora wdrażania aktualizacji oprogramowania lub Kreatora tworzenia zasady aktualizacji automatycznych.  

### <a name="deployment-reevaluation-cycle"></a>Cykl ponownego oszacowania wdrożenia  
 Domyślnie cykl ponownego oszacowania wdrożenia będzie powtarzany na komputerach klienckich co 7 dni. Podczas cyklu oszacowania komputer kliencki przeprowadzi skanowanie w poszukiwaniu uprzednio wdrożonych i zainstalowanych aktualizacji oprogramowania. W przypadku stwierdzenia braku jakichś aktualizacji oprogramowania zostaną one zainstalowane ponownie z lokalnej pamięci podręcznej. Jeśli aktualizacja oprogramowania nie będzie już dostępna w lokalnej pamięci podręcznej, zostanie pobrana z punktu dystrybucji, a następnie zainstalowana. Harmonogram ponownego oszacowania można skonfigurować na stronie **Aktualizacje oprogramowania** ustawień klienta lokacji.  

##  <a name="BKMK_EmbeddedDevices"></a> Obsługa urządzeń z systemem Windows Embedded używających filtrów zapisu  
 Wdrażając aktualizacje oprogramowania na urządzeniach z systemem Windows Embedded z włączoną obsługą filtru zapisu, można określić, czy podczas wdrażania wyłączyć filtr zapisu na urządzeniu, a następnie po zakończonym wdrażaniu ponownie uruchomić urządzenie. Jeśli filtr zapisu nie zostanie wyłączony, oprogramowanie zostanie wdrożone w tymczasowej nakładce i nie zostanie zainstalowane po ponownym uruchomieniu urządzenia, jeśli inne wdrożenie nie wymusi utrwalenia zmian.  

> [!NOTE]  
>  Po wdrożeniu aktualizacji oprogramowania do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi. Pozwoli to zarządzać czasem włączania i wyłączania filtru zapisu oraz czasem ponownego uruchomienia urządzenia.  

 Ustawienie czynności użytkownika kontrolujące zachowanie filtra zapisu ma postać pola wyboru o nazwie **Zatwierdź zmiany po upływie terminu wdrożenia lub w oknach obsługi (wymaga ponownego uruchomienia)**.  

 Aby uzyskać więcej informacji o zarządzaniu programu Configuration Manager na urządzeniach osadzonych korzystających z filtrów zapisu, zobacz [Planowanie wdrożenia klientów na urządzeniach Windows Embedded](../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

##  <a name="BKMK_ExtendSoftwareUpdates"></a> Rozszerzanie aktualizacji oprogramowania w programie Configuration Manager  
 System Center Updates Publisher umożliwia zarządzanie aktualizacjami oprogramowania, które nie są dostępne z witryny Microsoft Update. Po opublikowaniu aktualizacji oprogramowania na serwerze aktualizacji i synchronizować aktualizacje oprogramowania w programie Configuration Manager, można wdrożyć aktualizacje oprogramowania do klientów programu Configuration Manager. Aby uzyskać więcej informacji dotyczących programu Updates Publisher, zobacz [Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=252947).  

## <a name="next-steps"></a>Następne kroki
[Planowanie aktualizacji oprogramowania](../plan-design/plan-for-software-updates.md)
