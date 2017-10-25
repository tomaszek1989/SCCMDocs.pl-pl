---
title: "Planowanie zadań migracji | Dokumentacja firmy Microsoft"
description: "Aby skonfigurować dane, które chcesz migrować do środowiska programu System Center Configuration Manager, należy użyć zadania migracji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a70bfbd4-757a-4468-9312-1c3b373ef9fc
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex
ms.openlocfilehash: 4c83540db763bea039a92633a1d1a808e60e27ad
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="plan-a-migration-job-strategy-in-system-center-configuration-manager"></a>Planowanie strategii zadania migracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby skonfigurować określone dane, które chcesz migrować do środowiska programu System Center Configuration Manager, należy użyć zadania migracji. Zadania migracji zidentyfikować obiekty, które mają zostać poddane migracji, i są one uruchamiane w lokacji najwyższego poziomu w hierarchii docelowej. Można skonfigurować co najmniej jedno zadanie migracji na lokację źródłową. Umożliwia to migrację wszystkich obiektów w tym samym czasie lub Dobranie odpowiednich podzbiorów danych do każdego zadania.  

 Można utworzyć zadania migracji, po programu Configuration Manager pomyślnym zebraniu danych z przynajmniej jednej lokacji z hierarchii źródłowej. Dane z lokacji źródłowych, w których zebrano dane, można migrować w dowolnej kolejności. Z lokacji źródłowej programu Configuration Manager 2007 można migrować dane z witryny, w której został utworzony obiekt. Z lokacji źródłowych z systemem System Center 2012 Configuration Manager lub nowszego, wszystkie dane, które można migrować jest dostępna w lokacji najwyższego poziomu hierarchii źródłowej.  

 Przed migracją klientów między hierarchiami należy upewnić się, czy obiekty używane przez klientów zostały zmigrowane i czy są dostępne w hierarchii docelowej. Na przykład w przypadku migracji z hierarchii źródłowej programu Configuration Manager 2007 z dodatkiem SP2, może mieć anons zawartości wdrożonej do kolekcji niestandardowej zawierającej klienta. W tym scenariuszu zalecamy migracji kolekcję, anons i powiązaną zawartość przed przeprowadzeniem migracji klienta. Dane te nie zostaną skojarzone z klientem w hierarchii docelowej, jeśli zawartość, Kolekcja i anonse nie zostaną zmigrowane przed migracja klienta. Brak skojarzenia klienta z danymi powiązanymi z poprzednio uruchomionymi anonsami i zawartością może oznaczać, że klientowi zostanie zaoferowana zawartość do instalacji w hierarchii docelowej. Nie jest to konieczne. Migracja klienta po migracji danych oznacza, że klient zostanie skojarzony z tą zawartością i tym anonsem. O ile anons nie jest cykliczny, klientowi nie zostanie zaoferowana dana ponownie zawartość ze zmigrowanego anonsu.  

 Niektóre obiekty wymagają nie tylko migracji danych z hierarchii źródłowej do hierarchii docelowej. Na przykład do pomyślnej migracji aktualizacji oprogramowania dla klientów do hierarchii docelowej, możesz musi wdrożyć punkt aktualizacji oprogramowania aktywnego, skonfigurować katalog produktów i zsynchronizować punkt aktualizacji oprogramowania z systemu Windows Server Update Services (WSUS) w hierarchii docelowej.  

 Następujące sekcje są pomocne w planowaniu zadań migracji.  

-   [Rodzaje zadań migracji](#Types_of_Migration)  

-   [Planowanie ogólne wszystkich zadań migracji](#About_Migration_Jobs)  

-   [Planowanie zadań migracji kolekcji](#About_Collection_Migration)  

-   [Planowanie zadań migracji obiektów](#About_Object_Migration)  

-   [Planowanie poprzednio zmigrowanych zadania migracji obiektów](#About_Object_Migrations)  

##  <a name="Types_of_Migration"></a>Rodzaje zadań migracji  
 Configuration Manager obsługuje następujące rodzaje zadań migracji. Każdy typ zadania jest zaprojektowany z myślą o określeniu obiektów, które można uwzględnić w danym zadaniu.  

 **Migracja kolekcji** (obsługiwana tylko w przypadku migracji z programu Configuration Manager 2007 z dodatkiem SP2): Migrację obiektów, które są powiązane z wybranymi kolekcjami. Domyślnie migracja kolekcji obejmuje wszystkie obiekty, które są skojarzone z elementów kolekcji. Wykonując zadanie migracji kolekcji, można wykluczyć określone wystąpienia obiektów.  

 **Migracja obiektów**: Migracja poszczególnych wybranych obiektów. Obsługa wyboru konkretnych dane do migracji.  

 **Migracja uprzednio zmigrowanych obiektów**: Migrację obiektów, które zostały już uprzednio zmigrowane zostały zaktualizowane w hierarchii źródłowej po ostatniej migracji.  

###  <a name="Objects_that_can_migrate"></a>Obiekty, które można migrować  
 Nie każdy obiekt może zostać zmigrowany w określonym typie zadania migracji. Poniższa lista wskazuje typy obiektów, które można migrować za pomocą poszczególnych typów zadań migracji.  

> [!NOTE]  
>  Zadania migracji kolekcji są dostępne tylko w przypadku migracji obiektów z hierarchii źródłowej programu Configuration Manager 2007 z dodatkiem SP2.  

 **Typy zadań, które służy do migrowania poszczególnych obiektów**  

-   **Anonse** (dostępne do migracji z obsługiwanych lokacji źródłowych programu Configuration Manager 2007)  

    -   Migracja kolekcji  


-   **Katalog analizy zasobów**  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Wymagania sprzętowe analizy zasobów**  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Lista oprogramowania analizy zasobów**  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Granice**  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Linie bazowe konfiguracji**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Elementy konfiguracji**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Okna obsługi**  

    -   Migracja kolekcji  


-   **Obrazy rozruchowe wdrożeń systemu operacyjnego**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Pakiety sterowników wdrażania systemu operacyjnego**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Sterowniki wdrażania systemu operacyjnego**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Obrazy wdrożeń systemu operacyjnego**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Pakiety wdrażania systemu operacyjnego**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Pakiety dystrybucji oprogramowania**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Zasady pomiaru użytkowania oprogramowania**  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Pakiety wdrożeniowe aktualizacji oprogramowania**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Szablony wdrażania aktualizacji oprogramowania**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Wdrożenia aktualizacji oprogramowania**  

    -   Migracja kolekcji  


-   **Listy aktualizacji oprogramowania**  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Sekwencje zadań**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    -   Migracja uprzednio zmigrowanych obiektów  

-   **Pakiety aplikacji wirtualnych**  

    -   Migracja kolekcji  

    -   Migracja obiektów  

    > [!IMPORTANT]  
    >  Chociaż migrację pakietu z aplikacją wirtualną można wykonać za pomocą migracji obiektu, to nie jest możliwa migracja pakietów za pomocą typu zadania **Migracja uprzednio zmigrowanych obiektów**. Zamiast tego należy usunąć zmigrowany pakiet aplikacji wirtualnej z lokacji docelowej oraz utworzyć nowe zadanie migracji aplikacji wirtualnej.  

##  <a name="About_Migration_Jobs"></a>Planowanie ogólne wszystkich zadań migracji  
 Kreator tworzenia zadania migracji można utworzyć zadania migracji obiektów do hierarchii docelowej. Typ utworzonego zadania migracji określa obiekty dostępne do migracji. Możesz utworzyć i użyć wielu zadań migracji, aby przeprowadzić migrację danych z tej samej lokacji źródłowej lub z wielu lokacji źródłowych. Użycie jednego typu zadania migracji nie blokuje migracji za pomocą zadania innego typu.  

 Po pomyślnym uruchomieniu zadania migracji jego stan jest przedstawiony jako **Zakończono**. Ponowne uruchomienie takiego zadania nie jest możliwe. Jednak można utworzyć nowe zadanie migracji obejmujące obiekty, które zostały zmigrowane w oryginalnym zadaniu. Do nowego zadania można dołączyć dodatkowe obiekty. Po utworzeniu dodatkowych zadań migracji obiekty, które zostały już uprzednio zmigrowane, wyświetlić stan **zmigrowane**. Można wybrać te obiekty do migracji je ponownie, ale chyba, że obiekt został zaktualizowany w hierarchii źródłowej, ponownie migracji tych obiektów nie jest konieczne. Jeśli obiekt został zaktualizowany w hierarchii źródłowej po pierwotnej migracji, można go zidentyfikować, używając typu zadania dla migracji o nazwie **Obiekty zmodyfikowane po migracji**.  

 Przed uruchomieniem zadania migracji można je usunąć. Jednak po zakończeniu zadania migracji pozostaje widoczne w konsoli programu Configuration Manager i nie można go usunąć. Każde zadanie migracji, które zostało zakończone lub nie został jeszcze uruchomiony pozostaje widoczne w konsoli programu Configuration Manager do momentu zakończenia procesu migracji i wyczyść dane migracji.  

> [!NOTE]  
>  Po zakończeniu migracji za pomocą **Wyczyść dane migracji** można zrekonfigurować tę samą hierarchię jako bieżącą hierarchię źródłową. pozwoli to przywrócić widoczność obiektom wcześniej zostały zmigrowane.  

 Można wyświetlić obiekty należące do zadania migracji w konsoli programu Configuration Manager, wybierając zadanie migracji, a następnie wybierając **obiekty w zadaniu** kartę.  

 Informacje z poniższych sekcji pozwalają zaplanować wszystkie zadania migracji.  

### <a name="data-selection"></a>Wybór danych  
 Po utworzeniu zadania migracji kolekcji należy wybrać przynajmniej jedną kolekcję. Po wybraniu wszystkich kolekcji Kreator tworzenia zadania migracji zawiera obiekty, które są powiązane z kolekcjami. Domyślnie wszystkie obiekty skojarzone z wybranymi kolekcjami są migrowane, ale można usunąć zaznaczenie obiektów, których nie chcesz migrować za pomocą tego zadania. Te obiekty zależne możesz usunąć zaznaczenie pola wyboru obiektu, który ma obiekty zależne, również jest zaznaczony. Wszystkie obiekty usunięte zostaną dodane do listy wykluczeń. Obiekty na taj liście są automatycznie usuwane z zakresu automatycznego wyboru w przyszłych zadaniach migracji. Listę wykluczeń można ręcznie zmodyfikować tak, aby usunąć z niej obiekty, które mają być automatycznie uwzględnione w przyszłych zadaniach migracji.  

### <a name="site-ownership-for-migrated-content"></a>Własność lokacji dla zmigrowanej zawartości  
 Przeprowadzając migrację zawartości w celu jej wdrożenia, należy przypisać obiekt zawartości do lokacji w hierarchii docelowej. Ta lokacja stanie się następnie właścicielem treści w hierarchii docelowej. Chociaż migracja metadanych dotyczących zawartości jest wykonywana przez lokację najwyższego poziomu hierarchii docelowej, to przypisana lokacja uzyskuje dostęp do oryginalnych plików źródłowych zawartości w sieci.  

 Aby zminimalizować obciążenie przepustowości sieci podczas migrowania zawartości, warto zastanowić się nad przeniesieniem własności zawartości do najbliższej dostępnej lokacji. Ponieważ informacje o zawartości są udostępniane globalnie w programie System Center Configuration Manager, będzie dostępne w każdej lokacji.  

 Informacje o zawartości są udostępniane wszystkim lokacjom w hierarchii docelowej przy użyciu replikacji bazy danych. Jednak zawartość przypisać do lokacji głównej, a następnie wdrożona w punktach dystrybucji w innych lokacjach głównych będzie przesyłana przy przy użyciu replikacji opartej na plikach. Transfer jest kierowany przez centralną lokację administracyjną do każdej dodatkowej lokacji głównej. Centralizując pakiety przeznaczone do dystrybucji do wielu lokacji głównych przed lub w trakcie migracji po przypisaniu lokacji jako właściciela zawartości, można zredukować transfery danych w sieciach o niskiej przepustowości.  

### <a name="role-based-administration-security-scopes-for-migrated-data"></a>Zakresy zabezpieczeń administracji opartej na rolach dla migrowanych danych  
 Podczas migracji danych do hierarchii docelowej, należy przypisać co najmniej jeden administracji opartej na rolach na zakresy zabezpieczeń dla obiektów, których dane są migrowane. Dzięki temu tylko upoważnieni użytkownicy administracyjni będą mieli dostęp do danych po ich migracji. Określone zakresy zabezpieczeń są definiowane przez zadanie migracji i stosowane do każdego obiektu migrowanego w ramach danego zadania. Jeśli potrzebujesz różne zakresy zabezpieczeń stosowane do różnych zestawów obiektów i chcesz przypisać te zakresy podczas migracji, należy przeprowadzić migrację różnych zestawów obiektów przy użyciu różnych zadań migracji.  

 Przed skonfigurowaniem zadania migracji Przejrzyj administracji jak opartej na rolach działa w programie System Center Configuration Manager. Jeśli to konieczne, należy skonfigurować co najmniej jeden zakres zabezpieczeń dla danych migracji do kontrolowania, kto ma dostęp do zmigrowanych obiektów w hierarchii docelowej.  

 Aby uzyskać więcej informacji na temat zakresów zabezpieczeń i administracji opartej na rolach, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

### <a name="review-migration-actions"></a>Przeglądanie akcji związanych z migracją  
 Podczas konfigurowania zadania migracji Kreator tworzenia zadania migracji zawiera listę działań, które należy wykonać, aby zapewnić pomyślną migrację oraz listę działań, które programu Configuration Manager realizuje w trakcie migracji wybranych danych. Przejrzyj te informacje należy dokładnie sprawdzić oczekiwany wynik.  

### <a name="schedule-migration-jobs"></a>Zaplanuj zadania migracji  
 Domyślnie zadania migracji są uruchamiane bezpośrednio po ich utworzeniu. Można jednak określić po uruchomieniu zadania migracji, podczas tworzenia zadania lub zmienić przez edycję właściwości zadania. Można zaplanować zadanie migracji, aby uruchomić w następujący sposób:  

-   Uruchom zadanie teraz  

-   Uruchom zadanie o określonej godzinie rozpoczęcia  

-   Nie uruchamiaj zadania  

### <a name="specify-conflict-resolution-for-migrated-data"></a>Wybierz sposób rozwiązywania konfliktów dla migrowanych danych  
 Domyślnie zadania migracji nie zastępują danych w docelowej bazie danych dopiero po skonfigurowaniu zadania migracji, aby pomijać lub nadpisywać dane, które wcześniej zostały poddane migracji do docelowej bazy danych.  

##  <a name="About_Collection_Migration "></a>Planowanie zadań migracji kolekcji  
 Zadania migracji kolekcji są dostępne tylko w przypadku migracji danych z hierarchii źródłowej, która działa obsługiwana wersja programu Configuration Manager 2007. Podczas migracji kolekcji należy określić co najmniej jedną migrację, która ma być migrowana. W przypadku każdej określonej kolekcji zadanie migracji automatycznie wybierze do migracji wszystkie powiązane obiekty. Jeśli na przykład zostanie wybrana konkretna kolekcja użytkowników, nastąpi zidentyfikowanie członków tej kolekcji oraz będzie można migrować wdrożenia skojarzone z tą kolekcją. Opcjonalnie można wybrać do migracji także inne obiekty wdrożenia, które są skojarzone z tymi członkami. Wszystkie wybrane elementy są dodawane do listy obiektów przeznaczonych do migracji.  

 Podczas migracji kolekcji, System Center Configuration Manager migruje także ustawienia kolekcji, w tym okna obsługi i zmienne kolekcji, ale nie można migrować ustawień kolekcji dotyczących zapewniania udostępniania klientów AMT.  

 Skorzystaj z informacji w poniższych sekcjach, aby dowiedzieć się więcej o dodatkowych konfiguracjach, które można zastosować do zadania migracji kolekcji.  

### <a name="exclude-objects-from-collection-migration-jobs"></a>Wyklucz obiekty z zadań migracji kolekcji  
 Z zadania migracji kolekcji można wykluczyć konkretne obiekty. Po wykluczeniu konkretnego obiektu z zadania migracji kolekcji, ten obiekt jest dodawany do globalnej listy wykluczeń zawierający wszystkie obiekty, które zostały wykluczone z zadań migracji utworzonych dla dowolnej lokacji źródłowej w bieżącej hierarchii źródłowej. Obiekty na liście wykluczeń są nadal dostępne do migracji w przyszłych zadaniach, ale nie są automatycznie dołączane podczas tworzenia nowego zadania migracji kolekcji.  

 Listę wykluczeń można edytować w celu usuwania z niej obiektów, które zostały wcześniej wykluczone. Po usunięciu obiektu z listy wykluczeń będzie on automatycznie wybierany w przypadku wskazania skojarzonej z nim kolekcji podczas tworzenia nowego zadania migracji.  

### <a name="unsupported-collections"></a>Nieobsługiwane kolekcje  
 Menedżer konfiguracji można migrować wszystkie domyślne kolekcje użytkowników, kolekcje urządzeń oraz większość kolekcji niestandardowych z hierarchii źródłowej programu Configuration Manager 2007. Jednak programu Configuration Manager nie można migrować kolekcje zawierające użytkowników i urządzeń w tej samej kolekcji.  

 Nie można migrować następujących kolekcji:  

-   Kolekcja, która zawiera użytkowników i urządzeń.  

-   Kolekcja, która zawiera odwołanie do kolekcji inny typ zasobu. Na przykład kolekcji opartych na urządzeniach, która ma podkolekcję lub łącze do kolekcji użytkowników. W tym przykładzie przeprowadza migrację tylko kolekcja najwyższego poziomu.  

-   Kolekcja, która ma zasadę włączania nieznanych komputerów. Takie kolekcje są migrowane, ale bez zasady włączania nieznanych komputerów.  

### <a name="empty-collections"></a>Puste kolekcje  
 Pusta kolekcja to kolekcja, z którą nie są skojarzone żadne zasoby. W przypadku programu Configuration Manager migruje pustą kolekcję, konwertuje kolekcję do folderu organizacyjnego, który nie ma użytkowników ani urządzeń. Ten folder jest tworzony z nazwą pustej kolekcji w węźle **kolekcje użytkowników** lub **kolekcje urządzeń** w węźle **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  

### <a name="linked-collections-and-subcollections"></a>Połączone kolekcje i podkolekcje  
 Podczas migracji kolekcji, które są połączone z innymi kolekcjami lub zawierają podkolekcje, programu Configuration Manager tworzy folder w obszarze **kolekcje użytkowników** lub **kolekcje urządzeń** oprócz połączone kolekcje i podkolekcje.  

### <a name="collection-dependencies-and-include-objects"></a>Zależności kolekcji i uwzględniane obiekty  
 Po określeniu w kreatorze tworzenia zadania migracji kolekcji, wszystkie zależne kolekcje zostaną zaznaczone automatycznie zostanie uwzględniona w zadaniu. Takie zachowanie gwarantuje, ze po migracji będą dostępne wszystkie niezbędne zasoby.  

 Na przykład: Wybierz kolekcję urządzeń z systemem Windows 7 i nosi nazwę **Win_7**. Ta kolekcja jest ograniczona do kolekcji wszystkie systemy operacyjne klienta i nosi nazwę **All_Clients**. Kolekcja **All_Clients** zostanie automatycznie wybrana do migracji.  

### <a name="collection-limiting"></a>Ograniczanie kolekcji  
 Z programem System Center Configuration Manager kolekcje są danymi globalnymi i są oceniane w każdej lokacji w hierarchii. Dlatego też należy zaplanować, jak ograniczyć zakres kolekcji po ich migracji. Podczas migracji można zidentyfikować kolekcje z hierarchii docelowej, które mogą być użyte do ograniczenia zakresu migrowanych kolekcji. Dzięki temu zmigrowane kolekcje nie będą zawierać nieoczekiwanych członków.  

 Na przykład w programie Configuration Manager 2007 kolekcje są oceniane w lokacji, w której zostały utworzone i w lokacjach podrzędnych. W lokacji podrzędnej można wdrożyć anons, co powoduje ograniczenie zakresu tego anonsu do tej lokacji podrzędnej. W porównaniu z programem System Center Configuration Manager kolekcje są oceniane w każdej lokacji, a następnie skojarzone anonse są oceniane oddzielnie dla każdej lokacji. Ograniczanie kolekcji pozwala wykluczać członków kolekcji na podstawie innej kolekcji, tak aby uniknąć dodawania nieoczekiwanych członków kolekcji.  

### <a name="site-code-replacement"></a>Zastąpienie kodów lokacji  
 Podczas migracji kolekcji zawierającej kryteria identyfikujące lokację programu Configuration Manager 2007, należy określić konkretną lokację w hierarchii docelowej. Dzięki temu migrowana kolekcja będzie działać w hierarchii docelowej i nie spowoduje zwiększenia zakresu.  

### <a name="specify-behavior-for-migrated-advertisements"></a>Określenie zachowania migrowanych anonsów  
 Domyślnie zadania migracji kolekcji anonse nie są migrowane do hierarchii docelowej. Dotyczy to wszystkich programów skojarzonych z anonsami. Podczas tworzenia zadania migracji kolekcji zawierającej anonse, zobacz **Włącz programy wdrożenia w programie Configuration Manager po zmigrowaniu anonsu** opcja **ustawienia** w kreatorze tworzenia zadania migracji. Po zaznaczeniu tej opcji programy skojarzone z anonsem zostaną włączone po zmigrowaniu. Najlepszym rozwiązaniem nie należy zaznaczać tej opcji. Zamiast tego należy włączyć te programy dopiero po ich zmigrowaniu, gdy jest możliwe zweryfikowanie klientów, którzy będą otrzymywać je.  

> [!NOTE]  
>  Zostanie wyświetlony **Włącz programy wdrożenia w programie Configuration Manager po zmigrowaniu anonsu** opcję tylko podczas tworzenia zadania migracji kolekcji i zadania migracji zawiera anonse.  

 Aby włączyć program po migracji, usuń zaznaczenie **Wyłącz ten program na komputerach, na których jest anonsowany** na **zaawansowane** karcie we właściwościach programu.  

##  <a name="About_Object_Migration"></a>Planowanie zadań migracji obiektów  
 W przeciwieństwie do migracji kolekcji jest konieczne wybieranie poszczególnych obiektów i wystąpień obiektów przeznaczonych do migracji. Można wybierać pojedyncze obiekty, takie jak (anonse z hierarchii programu Configuration Manager 2007) lub publikacje z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager do dodania do listy obiektów migrowanych w konkretnym zadaniu migracji. Wszelkie obiekty, które nie zostaną dodane do listy migracji, nie zostaną zmigrowane do lokacji docelowej w tym zadaniu migracji obiektów.  

 Zadania migracji obiektów nie ma żadnych dodatkowych konfiguracji oprócz tych, które są stosowane do wszystkich zadań migracji.  

##  <a name="About_Object_Migrations"></a>Planowanie zadań migracji poprzednio zmigrowanych obiektów  
 Gdy w hierarchii źródłowej jest aktualizowany obiekt, który został już zmigrowany do hierarchii docelowej, można go ponownie zmigrować za pomocą typu zadania **Obiekty zmodyfikowane po migracji**. Na przykład po zmiany nazwy lub zaktualizowaniu plików źródłowych dla pakietu w hierarchii źródłowej, zwiększa się wersja pakietu w hierarchii źródłowej. Po zwiększeniu wersji pakietu może on zostać zidentyfikowany przez zadanie tego typu jako nadający się do migracji.  

 Ten typ zadania jest podobny do typu migracji obiektów, jednak podczas wybierania migrowanych obiektów można wybierać tylko obiekty zaktualizowane po poprzedniej migracji wykonywanej za pomocą poprzedniego zadania migracji.   

 Po wybraniu tego typu zadania zachowanie rozwiązywania konfliktów na **ustawienia** w kreatorze tworzenia zadania migracji jest konfigurowane do zastępowania poprzednio zmigrowanych obiektów. Nie można zmienić tego ustawienia.  

> [!NOTE]  
>  To zadanie migracji może identyfikować obiekty, które zostały automatycznie zaktualizowane przez hierarchię źródłową, oraz obiekty zaktualizowane przez użytkownika administracyjnego.  
