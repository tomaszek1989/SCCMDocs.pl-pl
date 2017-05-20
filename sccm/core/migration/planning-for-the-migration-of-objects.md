---
title: "Migracja obiektów | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak planowanie migracji obiektów między hierarchiami w środowisku programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45931f60273f3130cca36320770126a36dcc3d1e
ms.openlocfilehash: 9870ffa6ae5f80db823bfc74a7cc2e67fc8cf21d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-migration-of-configuration-manager-objects-to-system-center-configuration-manager"></a>Planowanie migracji obiektów programu Configuration Manager programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą programu System Center Configuration Manager można migrować wiele różnych obiektów, które są skojarzone z różnymi funkcjami znalezionymi w lokacji źródłowej. Informacje w poniższych sekcjach ułatwią planowanie migracji obiektów między hierarchiami.  

-   [Planowanie migracji aktualizacji oprogramowania](#Plan_migrate_Software_updates)  

-   [Planowanie migracji zawartości](#Plan_Migrate_content)  

-   [Planowanie migracji kolekcji](#BKMK_MigrateCollections)  

-   [Planowanie migracji wdrożeń systemu operacyjnego](#Plan_migrate_OSD)  

-   [Planowanie migracji zarządzania żądaną konfiguracją](#Plan_Migrate_Compliance_settings)  

-   [Planowanie migracji granic](#Plan_migrate_Boundaries)  

-   [Planowanie migracji raportów](#Plan_Migrate_reports)  

-   [Planowanie do migracji folderów wyszukiwania i organizacyjnych](#Plan_Migrate_Org_Folders)  

-   [Planowanie migracji dostosowań analizy zasobów](#Plan_Migrate_AI)  

-   [Planowanie migracji dostosowań zasad pomiaru użytkowania oprogramowania](#Plan_Migrate_SWM_Rules)  

##  <a name="Plan_migrate_Software_updates"></a>Planowanie migracji aktualizacji oprogramowania  
 Można migrować obiekty aktualizacji oprogramowania, takie jak pakiety aktualizacji oprogramowania i wdrożenia aktualizacji oprogramowania.  

 Aby pomyślnie przeprowadzić migrację obiektów aktualizacji oprogramowania, należy najpierw skonfigurować hierarchię docelową z konfiguracjami, które odpowiadają środowiskiem hierarchii źródłowej. Wymaga to wykonania następujących akcji:  

-   Wdrożenie punktu aktualizacji oprogramowania aktywnego w hierarchii docelowej  

-   Konfigurowanie katalogu produktów i języków zgodnie z konfiguracją hierarchii źródłowej  

-   Synchronizacja punktu aktualizacji oprogramowania w hierarchii docelowej z systemu Windows serwera Update Services (WSUS)  

Podczas migracji aktualizacji oprogramowania należy uwzględnić następujące kwestie:  

-   Migracja obiektów aktualizacji oprogramowania może zakończyć się niepowodzeniem, gdy informacje nie zostały zsynchronizowane w hierarchii docelowej zgodnie z konfiguracją hierarchii źródłowej.  

    > [!WARNING]  
    >  Menedżer konfiguracji nie obsługuje użycie narzędzia WSUSutil do synchronizacji danych między hierarchią źródłową i docelową.  

-   Nie można migrować aktualizacji niestandardowych opublikowanych przy użyciu programu System Center Updates Publisher. Zamiast tego należy ponownie opublikować aktualizacje niestandardowe w hierarchii docelowej.  

W przypadku migracji z hierarchii źródłowej programu Configuration Manager 2007, proces migracji modyfikuje niektóre obiekty aktualizacji oprogramowania do formatu używanego przez hierarchię docelową. Skorzystaj z poniższej tabeli ułatwią planowanie migracji obiektów aktualizacji oprogramowania z programu Configuration Manager 2007.  

|Obiekt programu Configuration Manager 2007|Nazwa obiektu po migracji|  
|-----------------------------------|---------------------------------|  
|Listy aktualizacji oprogramowania|Listy aktualizacji oprogramowania są konwertowane na grupy aktualizacji oprogramowania.|  
|Wdrożenia aktualizacji oprogramowania|Wdrożenia aktualizacji oprogramowania są konwertowane na wdrożenia i grupy aktualizacji.<br /><br /> Po przeprowadzeniu migracji wdrożenia aktualizacji oprogramowania z programu Configuration Manager 2007, należy włączyć ją w hierarchii docelowej, zanim będzie można go wdrożyć.|  
|Pakiety aktualizacji oprogramowania|Pakiety aktualizacji oprogramowania nie ulegają zmianie.|  
|Szablony aktualizacji oprogramowania|Szablony aktualizacji oprogramowania nie ulegają zmianie.<br /><br /> **Czas trwania** wartość w szablonach wdrożenia programu Configuration Manager 2007 nie jest migrowana.|  

Przy migracji obiektów z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, obiekty aktualizacji oprogramowania nie są modyfikowane.  

##  <a name="Plan_Migrate_content"></a>Planowanie migracji zawartości  
 Zawartość można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej. W hierarchii źródłowej programu Configuration Manager 2007 ta zawartość obejmuje pakiety dystrybucji oprogramowania oraz programy i aplikacje wirtualne, takie jak Microsoft Application Virtualization (App-V). System Center 2012 Configuration Manager i System Center Configuration Manager hierarchii źródłowej ta zawartość obejmuje aplikacje i aplikacje wirtualne App-V. Podczas migrowania zawartości między hierarchiami skompresowane pliki źródłowe migracji do hierarchii docelowej.  

### <a name="packages-and-programs"></a>Pakiety i programy  
 Migracja nie powoduje modyfikacji pakietów i programów. Jednak przed ich migracją, możesz należy skonfigurować każdy pakiet, aby używał ścieżki Universal Naming Convention (UNC) dla lokalizacji pliku źródłowego. W ramach konfigurowania migracji pakietów i programów należy przypisać w hierarchii docelowej lokację, która będzie zarządzać tą zawartością. Zawartość nie jest migrowana z przypisanej lokacji, ale po migracji, przypisana lokacja uzyskuje dostęp do lokalizacji oryginalnego pliku źródłowego, używając mapowania UNC.  

 Po przeprowadzeniu migracji pakietu i programu do hierarchii docelowej i gdy migracja z hierarchii źródłowej pozostaje aktywna, można można udostępnić zawartość klientom w tej hierarchii za pomocą współużytkowanego punktu dystrybucji. Aby można było użyć współużytkowanego punktu dystrybucji, zawartość musi pozostać dostępna w punkcie dystrybucji w lokacji źródłowej. Aby uzyskać więcej informacji o współużytkowanych punktów dystrybucji, zobacz [udostępniać punktów dystrybucji między hierarchiami źródłową i docelową](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) w [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

 Dla zawartości migrowanej, jeśli zmiany wersji zawartości w hierarchii źródłowej lub docelowej, klienci nie mają dostęp do zawartości z punktu dystrybucji w hierarchii docelowej. W tym scenariuszu należy ponownie migrować zawartość, aby przywrócić wersję spójną pakietu między hierarchią źródłową i hierarchią docelową. Te informacje jest synchronizowane podczas cyklu zbierania danych.  

> [!TIP]  
>  Dla każdego migrowanego pakietu zaktualizuj pakiet w hierarchii docelowej. Ta akcja może zapobiec problemom dotyczącym wdrażania pakietu w punktach dystrybucji w hierarchii docelowej. Jednak po zaktualizowaniu pakietu w punkcie dystrybucji w hierarchii docelowej klienci w tej hierarchii nie będą już mogli uzyskać tego pakietu ze współużytkowanego punktu dystrybucji. Aby zaktualizować pakiet w hierarchii docelowej w konsoli programu Configuration Manager, przejdź do biblioteki oprogramowania, kliknij prawym przyciskiem myszy pakiet, a następnie wybierz **Aktualizuj punkty dystrybucji**. Wykonaj tę akcję dla każdego migrowanego pakietu.  

> [!TIP]  
>  Do konwersji pakietów i programów do aplikacji programu System Center Configuration Manager, można użyć Menedżera konwersji pakietu Microsoft System Center Configuration Manager. Program Package Conversion Manager można pobrać z witryny [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=212950). Aby uzyskać więcej informacji, zobacz [Program Configuration Manager Package Conversion Manager](http://go.microsoft.com/fwlink/p/?LinkId=247245).  

### <a name="virtual-applications"></a>Aplikacje wirtualne  
Pakiety App-V w przypadku migracji z obsługiwanej lokacji programu Configuration Manager 2007, proces migracji powoduje ich konwersję do aplikacji w hierarchii docelowej. Ponadto na podstawie istniejących anonsów pakietu aplikacji App-V, są tworzone następujące typy wdrożeń w hierarchii docelowej:  

-   Jeżeli nie ma żadnych anonsów, tworzony jest jeden typ wdrożenia, który używa domyślnych ustawień typu wdrożenia.  

-   Jeżeli istnieje jeden anons, tworzony jest jeden typ wdrożenia, który używa tych samych ustawień co anons programu Configuration Manager 2007.  

-   Jeśli istnieje kilka anonsów, typ wdrożenia jest utworzone dla każdego anonsu programu Configuration Manager 2007 przy użyciu ustawień tego anonsu.  

> [!IMPORTANT]  
>  Jeśli migracja uprzednio zmigrowanych pakietu programu Configuration Manager 2007 App-V, migracja nie powiedzie się, ponieważ pakiety aplikacji wirtualnej nie obsługują migracji zastępującej. W tym scenariuszu należy usunąć migrowany pakiet aplikacji wirtualnej z hierarchii docelowej, a następnie utworzyć nowe zadanie migracji w celu migracji aplikacji wirtualnej.  

> [!NOTE]  
>  Po migrowania pakietu App-V można użyć Kreatora aktualizacji zawartości zmienić ścieżkę źródłową typów wdrożeń App-V. Więcej informacji o sposobie aktualizowania zawartości dla typu wdrożenia znajduje się w temacie jak zarządzać typami wdrożeń w [zadania zarządzania dla programu System Center Configuration Manager aplikacji](../../apps/deploy-use/management-tasks-applications.md).  

W przypadku migracji z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, można migrować obiekty dla środowiska wirtualnego App-V, oprócz typów wdrożeń App-V i aplikacji. Aby uzyskać więcej informacji o środowiskach App-V, zobacz [aplikacje wirtualne App-V wdrażanie z System Center Configuration Manager](../../apps/get-started/deploying-app-v-virtual-applications.md).  

### <a name="advertisements"></a>Anonse  
Za pomocą migracji kolekcji anonse można migrować z obsługiwanej lokacji źródłowej programu Configuration Manager 2007 do hierarchii docelowej. Po uaktualnieniu klienta zachowuje on historię poprzednio uruchomionych anonsów, aby zapobiec ponownemu uruchomieniu przez klienta migrowanych anonsów.  

> [!NOTE]  
>  Nie można migrować anonsów dla pakietów wirtualnych. Jest to wyjątek dotyczący migracji anonsów.  

### <a name="applications"></a>Aplikacje  
 Aplikacje można migrować z obsługiwanej hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager do hierarchii docelowej. Po ponownym przypisaniu klienta z hierarchii źródłowej do hierarchii docelowej zachowuje on historię poprzednio zainstalowanych aplikacji, aby zapobiec ponownemu uruchomieniu migrowanych aplikacji.  

##  <a name="BKMK_MigrateCollections"></a>Planowanie migracji kolekcji  
 Kryteria kolekcji można migrować z obsługiwanej hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager. W tym celu należy użyć zadania migracji obiektów. Migracja kolekcji oznacza migrację jej zasad, a nie informacji o członkach kolekcji ani informacji lub obiektów dotyczących członków kolekcji.  

 Migracja obiektu kolekcji nie jest obsługiwana w przypadku migracji z hierarchii źródłowej programu Configuration Manager 2007.  

##  <a name="Plan_migrate_OSD"></a>Planowanie migracji wdrożeń systemu operacyjnego  
Z obsługiwanej hierarchii źródłowej można migrować następujące obiekty wdrożenia systemu operacyjnego:  

-   Obrazy i pakiety systemów operacyjnych. Ścieżka źródłowa obrazów rozruchowych jest aktualizowane do domyślnej lokalizacji obraz dla systemu Windows zestawu Administrative Installation Kit (Windows AIK) w lokacji docelowej. Poniżej przedstawiono wymagania i ograniczenia dotyczące migracji obrazów i pakietów systemu operacyjnego:  

    -   Aby pomyślnie migrować pliki obrazów, konto komputera serwera dostawcy programu SMS dla lokacji najwyższego poziomu w hierarchii docelowej musi mieć **odczytu** i **zapisu** uprawnienia do plików źródłowych obrazu w lokacji źródłowej lokalizacji zestawu Windows AIK.  

    -   W przypadku migracji pakietu instalacyjnego systemu operacyjnego, upewnij się, że konfiguracja pakietu lokacji źródłowej wskazuje folder zawierający plik WIM, a nie sam plik WIM. Jeżeli pakiet instalacji wskazuje plik WIM, migracja pakietu instalacji nie powiedzie się.  

    -   W przypadku migracji pakietu obrazu rozruchowego z lokacji źródłowej programu Configuration Manager 2007, identyfikator pakietu pakietu nie jest zachowywany w lokacji docelowej. Z tego powodu klienci w hierarchii docelowej nie mogą użyć pakietów obrazu rozruchowego dostępnych we współużytkowanych punktach dystrybucji.  

-   Sekwencje zadań. W przypadku migracji sekwencji zadań, która zawiera odwołanie do pakietu instalacyjnego klienta, została zastąpiona odwołującymi się odwołanie do pakietu instalacyjnego klienta w hierarchii docelowej.  

    > [!NOTE]  
    >  W przypadku migracji sekwencji zadań, programu Configuration Manager może migrować obiekty, które nie są wymagane w hierarchii docelowej. Te obiekty obejmują obrazy rozruchowe i pakiety instalacyjne klienta programu Configuration Manager 2007.  

-   Sterowniki i pakiety sterowników.  

##  <a name="Plan_Migrate_Compliance_settings"></a>Planowanie migracji zarządzania żądaną konfiguracją  
Można migrować elementy konfiguracji i linie bazowe konfiguracji.  

> [!NOTE]  
>  Niezinterpretowanych elementów konfiguracji z hierarchii źródłowej programu Configuration Manager 2007 nie są obsługiwane dla migracji. Nie można migrować ani importować tych elementów konfiguracji do hierarchii docelowej. Aby uzyskać więcej informacji o niezinterpretowanych elementów konfiguracji, zobacz Niezinterpretowanych elementów konfiguracji w [About Configuration Items in Desired Configuration Management](http://go.microsoft.com/fwlink/?LinkId=103846) w bibliotece dokumentacji programu Configuration Manager 2007.  

Można importować pakiety konfiguracyjne programu Configuration Manager 2007. Proces importowania powoduje automatyczną konwersję pakietów konfiguracyjnych, aby był zgodny z System Center Configuration Manager.  

##  <a name="Plan_migrate_Boundaries"></a>Planowanie migracji granic  
 Granice można migrować między hierarchiami. Podczas migracji z programu Configuration Manager 2007, wszystkie granice z lokacji źródłowej migracji w tym samym czasie i jest dodawany do nowej grupy granic utworzonej w hierarchii docelowej. Podczas migracji z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager, każda wybrana granica jest dodawany do nowej grupy granic w hierarchii docelowej.  

 Każda automatycznie utworzona grupa granic może być lokalizacją zawartości, jednak nie może być używana do przypisywania lokacji. Zapobiega to nakładaniu się granic podczas przypisywania lokacji między hierarchiami źródłową i docelową. W przypadku migracji z lokacji źródłowej programu Configuration Manager 2007 pomaga zapobiegać nowych klientów programu Configuration Manager 2007, które zainstalować nieprawidłowemu przypisywaniu do hierarchii docelowej. Domyślnie klienci programu System Center Configuration Manager nie są automatycznie przypisywani do lokacji programu Configuration Manager 2007.  

 Podczas migracji, jeśli współużytkujesz punkt dystrybucji z hierarchią docelową, wszystkie granice skojarzone z tą dystrybucją automatycznie migrują do hierarchii docelowej. W hierarchii docelowej proces migracji tworzy nową grupę granic tylko do odczytu dla każdego współużytkowanego punktu dystrybucji. Jeśli zmienisz granice punktu dystrybucji w hierarchii źródłowej, grupa granic w hierarchii docelowej zostanie zaktualizowana tymi zmianami podczas następnego cyklu zbierania danych.  

##  <a name="Plan_Migrate_reports"></a>Planowanie migracji raportów  
Menedżer konfiguracji nie obsługuje migracji raportów. W tej sytuacji raporty można eksportować z hierarchii źródłowej za pomocą narzędzia SQL Server Reporting Services Report Builder, a następnie zaimportować je do hierarchii docelowej.  

> [!NOTE]  
>  Ponieważ istnieją zmiany schematu dla między wersjami programu Configuration Manager 2007 i programu System Center Configuration Manager, należy przetestować każdy raport zaimportowany z hierarchii programu Configuration Manager 2007, aby upewnić się, że działa zgodnie z oczekiwaniami.  

Aby uzyskać więcej informacji o raportach zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="Plan_Migrate_Org_Folders"></a>Planowanie do migracji folderów wyszukiwania i organizacyjnych  
 Foldery organizacyjne i folder wyszukiwania można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej. Dodatkowo z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, kryteria dla zapisanego wyszukiwania można migrować do hierarchii docelowej.  

 Domyślnie proces migracji obsługuje obiekty i kolekcje ze struktur folderu wyszukiwania i folderu organizacyjnego. Jednak w kreatorze tworzenia zadania migracji na **ustawienia** strony, możesz tworzyć zadania migracji nie migracji organizacyjnej struktury obiektów, usuwając zaznaczenie pola pole dla tej opcji. Struktury organizacyjne kolekcji są zawsze obsługiwane.  

 Jedynym wyjątkiem jest folder wyszukiwania, który zawiera aplikacje wirtualne. Podczas migrowania pakietu App-V App-V jest on przekształcany w aplikację w programie System Center Configuration Manager. Po migracji folderu wyszukiwania są znajdowane tylko pozostałe pakiety, a folder wyszukiwania nie może zlokalizować pakietu App-V z powodu tej konwersji do aplikacji podczas migrowania pakietu App-V.  

 Podczas migracji zapisanego kryterium wyszukiwania z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, można migrować kryteria wyszukiwania, a nie informacje o wynikach wyszukiwania. Migracja zapisanego kryterium wyszukiwania nie ma zastosowania w lokacji źródłowej programu Configuration Manager 2007.  

##  <a name="Plan_Migrate_AI"></a>Planowanie migracji dostosowań analizy zasobów  
 Dostosowania analizy zasobów można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej. Nie wprowadzono żadnych ważnych zmian w strukturze dostosowań analizy zasobów między programu Configuration Manager 2007 i programu System Center Configuration Manager.  

> [!NOTE]  
>  System Center Configuration Manager nie obsługuje migracji obiektów analizy zasobów z lokacji programu Configuration Manager 2007, która używa usług analizy zasobów wersji 2.0 (AIS 2.0).  

##  <a name="Plan_Migrate_SWM_Rules"></a>Planowanie migracji dostosowań zasad pomiaru użytkowania oprogramowania  
 Nie wprowadzono żadnych istotnych zmian dotyczących pomiaru użytkowania oprogramowania między programu Configuration Manager 2007 i programu System Center Configuration Manager. Zasady pomiaru użytkowania oprogramowania można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej.  

 Domyślnie zasady pomiaru użytkowania oprogramowania, które można migrować do hierarchii docelowej, nie są skojarzone z konkretną lokacją w hierarchii docelowej, lecz mają zastosowanie do wszystkich klientów w hierarchii. Aby zastosować zasadę pomiaru użytkowania oprogramowania do klientów w konkretnej lokacji, należy edytować zasadę pomiaru po jej zmigrowaniu.  

