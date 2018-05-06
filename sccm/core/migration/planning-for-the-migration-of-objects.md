---
title: Migracja obiektów
titleSuffix: Configuration Manager
description: Dowiedz się, jak planowanie migracji obiektów między hierarchiami w środowisku programu System Center Configuration Manager.
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 066caf00-e419-4efb-93d3-ba4ba878297c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0e42b7c8db3ef8c6d645d29f371fd6da475159bd
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="plan-for-the-migration-of-configuration-manager-objects-to-system-center-configuration-manager"></a>Planowanie migracji obiektów programu Configuration Manager do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programem System Center Configuration Manager można migrować wiele różnych obiektów, które są skojarzone z różnymi funkcjami znalezionymi w lokacji źródłowej. Informacje w poniższych sekcjach ułatwią planowanie migracji obiektów między hierarchiami.  

-   [Planowanie migracji aktualizacji oprogramowania](#Plan_migrate_Software_updates)  

-   [Planowanie migracji zawartości](#Plan_Migrate_content)  

-   [Planowanie migracji kolekcji](#BKMK_MigrateCollections)  

-   [Planowanie migracji wdrożeń systemu operacyjnego](#Plan_migrate_OSD)  

-   [Planowanie migracji zarządzania wymaganą konfiguracją](#Plan_Migrate_Compliance_settings)  

-   [Planowanie migracji granic](#Plan_migrate_Boundaries)  

-   [Planowanie migracji raportów](#Plan_Migrate_reports)  

-   [Planowanie migracji folderów wyszukiwania i organizacyjnych](#Plan_Migrate_Org_Folders)  

-   [Planowanie migracji dostosowań analizy zasobów](#Plan_Migrate_AI)  

-   [Planowanie migracji dostosowań reguł pomiaru użytkowania oprogramowania](#Plan_Migrate_SWM_Rules)  

##  <a name="Plan_migrate_Software_updates"></a> Planowanie migracji aktualizacji oprogramowania  
 Można migrować obiekty aktualizacji oprogramowania, takie jak pakiety aktualizacji oprogramowania i wdrożenia aktualizacji oprogramowania.  

 Aby pomyślnie migrować obiekty aktualizacji oprogramowania, należy najpierw skonfigurować hierarchię docelową z konfiguracjami, które odpowiadają środowiskiem hierarchii źródłowej. Wymaga to wykonania następujących akcji:  

-   Wdrażanie aktywnego punktu aktualizacji oprogramowania w hierarchii docelowej  

-   Konfigurowanie katalogu produktów i języków odpowiadający konfiguracji hierarchii źródłowej  

-   Synchronizacji punktu aktualizacji oprogramowania w hierarchii docelowej z systemu Windows Server Update Services (WSUS)  

Podczas migracji aktualizacji oprogramowania należy uwzględnić następujące kwestie:  

-   Migracja obiektów aktualizacji oprogramowania może zakończyć się niepowodzeniem, gdy informacje nie zostały zsynchronizowane w hierarchii docelowej odpowiadający konfiguracji hierarchii źródłowej.  

    > [!WARNING]  
    >  Menedżer konfiguracji nie obsługuje użycia narzędzia WSUSutil do synchronizacji danych między hierarchią źródłową i docelową.  

-   Nie można migrować aktualizacji niestandardowych opublikowanych przy użyciu programu System Center Updates Publisher. Zamiast tego należy ponownie opublikować aktualizacje niestandardowe w hierarchii docelowej.  

W przypadku migracji z hierarchii źródłowej programu Configuration Manager 2007, proces migracji modyfikuje niektóre obiekty aktualizacji oprogramowania do formatu używanego przez hierarchię docelową. Skorzystaj z poniższej tabeli ułatwią planowanie migracji obiektów aktualizacji oprogramowania z programu Configuration Manager 2007.  

|Obiekt programu Configuration Manager 2007|Nazwa obiektu po migracji|  
|-----------------------------------|---------------------------------|  
|Listy aktualizacji oprogramowania|Listy aktualizacji oprogramowania są konwertowane na grupy aktualizacji oprogramowania.|  
|Wdrożenia aktualizacji oprogramowania|Wdrożenia aktualizacji oprogramowania są konwertowane na wdrożenia i grupy aktualizacji.<br /><br /> Po przeprowadzeniu migracji wdrożenia aktualizacji oprogramowania z programu Configuration Manager 2007, należy włączyć ją w hierarchii docelowej przed jego wdrożeniem.|  
|Pakiety aktualizacji oprogramowania|Pakiety aktualizacji oprogramowania nie ulegają zmianie.|  
|Szablony aktualizacji oprogramowania|Szablony aktualizacji oprogramowania nie ulegają zmianie.<br /><br /> **Czas trwania** wartość w szablonach wdrożenia programu Configuration Manager 2007 nie może przeprowadzić migracji.|  

Przy migracji obiektów z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, obiekty aktualizacji oprogramowania nie są modyfikowane.  

##  <a name="Plan_Migrate_content"></a> Planowanie migracji zawartości  
 Zawartość można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej. Dla hierarchii źródłowej programu Configuration Manager 2007 ta zawartość obejmuje pakiety dystrybucji oprogramowania oraz programy i aplikacje wirtualne, takie jak Microsoft Application Virtualization (App-V). Dla programu System Center 2012 Configuration Manager i System Center Configuration Manager hierarchii źródłowej ta zawartość obejmuje aplikacje i aplikacje wirtualne App-V. Podczas migrowania zawartości między hierarchiami, skompresowane pliki źródłowe migracji do hierarchii docelowej.  

### <a name="packages-and-programs"></a>Pakiety i programy  
 Migracja nie powoduje modyfikacji pakietów i programów. Jednakże przed ich migracją, należy skonfigurować każdy pakiet korzystającej ze ścieżki Universal Naming Convention (UNC) do lokalizacji pliku źródłowego. W ramach konfigurowania migracji pakietów i programów należy przypisać w hierarchii docelowej lokację, która będzie zarządzać tą zawartością. Zawartość nie jest migrowana z przypisanej lokacji, ale po migracji, przypisana lokacja uzyskuje dostęp do lokalizacji oryginalnych plików źródłowych przy użyciu mapowania UNC.  

 Po przeprowadzeniu migracji pakietu i programu do hierarchii docelowej, a podczas migracji z hierarchii źródłowej pozostaje aktywna, można udostępnić zawartość klientom w tej hierarchii przy użyciu współużytkowanego punktu dystrybucji. Aby można było użyć współużytkowanego punktu dystrybucji, zawartość musi pozostać dostępna w punkcie dystrybucji w lokacji źródłowej. Aby uzyskać więcej informacji o współużytkowanych punktów dystrybucji, zobacz [współużytkowane punkty dystrybucji między hierarchiami źródłową i docelową](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) w [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

 Dla zawartości migrowanej, jeśli zmiany wersji zawartości w hierarchii źródłowej lub hierarchii docelowej, klienci nie jest już dostęp do zawartości ze współużytkowanego punktu dystrybucji w hierarchii docelowej. W tym scenariuszu należy ponownie migrować zawartość, aby przywrócić zgodny wersji pakietu między hierarchią źródłową i hierarchią docelową. Te informacje jest synchronizowane podczas cyklu zbierania danych.  

> [!TIP]  
>  Dla każdego migrowanego pakietu zaktualizuj pakiet w hierarchii docelowej. Ta akcja może zapobiec problemom dotyczącym wdrażania pakietu w punktach dystrybucji w hierarchii docelowej. Jednak po zaktualizowaniu pakietu w punkcie dystrybucji w hierarchii docelowej, klienci w tej hierarchii nie będą już mieć możliwość pobrania tego pakietu ze współużytkowanego punktu dystrybucji. Aby zaktualizować pakiet w hierarchii docelowej, w konsoli programu Configuration Manager przejdź do biblioteki oprogramowania, kliknij prawym przyciskiem myszy pakiet, a następnie wybierz **Aktualizuj punkty dystrybucji**. Wykonaj tę akcję dla każdego migrowanego pakietu.  

> [!TIP]  
>  Microsoft System Center Configuration Manager Package Conversion Manager można użyć w celu skonwertowania pakietów i programów do aplikacji programu System Center Configuration Manager. Program Package Conversion Manager można pobrać z witryny [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=212950). Aby uzyskać więcej informacji, zobacz [Program Configuration Manager Package Conversion Manager](http://go.microsoft.com/fwlink/p/?LinkId=247245).  

### <a name="virtual-applications"></a>Aplikacje wirtualne  
Podczas migracji pakietów aplikacji App-V z obsługiwanej lokacji programu Configuration Manager 2007, proces migracji powoduje ich konwersję do aplikacji w hierarchii docelowej. Ponadto na podstawie istniejących anonsów pakietu aplikacji App-V, są tworzone następujące typy wdrożeń w hierarchii docelowej:  

-   Jeżeli nie ma żadnych anonsów, tworzony jest jeden typ wdrożenia, który używa domyślnych ustawień typu wdrożenia.  

-   Jeżeli istnieje jeden anons, tworzony jest jeden typ wdrożenia, który używa tych samych ustawień co anons programu Configuration Manager 2007.  

-   Jeśli istnieje kilka anonsów, typ wdrożenia jest tworzony dla każdego anonsu programu Configuration Manager 2007, korzystając z ustawień tego anonsu.  

> [!IMPORTANT]  
>  Jeśli migracja uprzednio zmigrowanych pakietu programu Configuration Manager 2007 App-V, migracja nie powiedzie się, ponieważ pakiety aplikacji wirtualnej nie obsługują migracji zastępującej. W tym scenariuszu należy usunąć migrowany pakiet aplikacji wirtualnej z hierarchii docelowej, a następnie utworzyć nowe zadanie migracji w celu migracji aplikacji wirtualnej.  

> [!NOTE]  
>  Po przeprowadzeniu migracji pakietu aplikacji App-V, służy Kreator aktualizacji zawartości można zmienić ścieżkę źródłową typów wdrożeń App-V. Aby uzyskać więcej informacji o sposobie aktualizowania zawartości dla typu wdrożenia, zobacz jak zarządzać typami wdrożeń w [zadania zarządzania dla aplikacji programu System Center Configuration Manager](../../apps/deploy-use/management-tasks-applications.md).  

W przypadku migracji z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, można migrować obiekty dla środowiska wirtualnego App-V oprócz typów wdrożeń App-V i aplikacji. Aby uzyskać więcej informacji o środowiskach App-V, zobacz [aplikacje wirtualne App-V wdrażania z System Center Configuration Manager](../../apps/get-started/deploying-app-v-virtual-applications.md).  

### <a name="advertisements"></a>Anonse  
Anonse można migrować z obsługiwanej lokacji źródłowej programu Configuration Manager 2007 do hierarchii docelowej, używając migracji opartej na kolekcji. Po uaktualnieniu klienta zachowuje on historię poprzednio uruchomionych anonsów, aby zapobiec ponownemu uruchomieniu przez klienta migrowanych anonsów.  

> [!NOTE]  
>  Nie można migrować anonsów dla pakietów wirtualnych. Jest to wyjątek dotyczący migracji anonsów.  

### <a name="applications"></a>Aplikacje  
 Aplikacje można migrować z obsługiwanej hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager do hierarchii docelowej. Po ponownym przypisaniu klienta z hierarchii źródłowej do hierarchii docelowej zachowuje on historię poprzednio zainstalowanych aplikacji, aby zapobiec ponownemu uruchomieniu migrowanych aplikacji.  

##  <a name="BKMK_MigrateCollections"></a> Planowanie migracji kolekcji  
 Kryteria kolekcji można migrować z obsługiwanej hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager. W tym celu należy użyć zadania migracji obiektów. Migracja kolekcji oznacza migrację jej zasad, a nie informacji o członkach kolekcji ani informacji lub obiektów dotyczących członków kolekcji.  

 Migracja obiektu kolekcji nie jest obsługiwana w przypadku migracji z hierarchii źródłowej programu Configuration Manager 2007.  

##  <a name="Plan_migrate_OSD"></a> Planowanie migracji wdrożeń systemu operacyjnego  
Z obsługiwanej hierarchii źródłowej można migrować następujące obiekty wdrożenia systemu operacyjnego:  

-   Obrazy i pakiety systemów operacyjnych. Ścieżka źródłowa obrazów rozruchowych jest aktualizowane do domyślnej lokalizacji obraz dla systemu Windows administracyjne zestawie instalacji (systemu Windows Windows AIK) w lokacji docelowej. Poniżej przedstawiono wymagania i ograniczenia dotyczące migracji obrazów i pakietów systemu operacyjnego:  

    -   Aby pomyślnie migrować pliki obrazów, konto komputera serwera dostawcy programu SMS dla lokacji najwyższego poziomu w hierarchii docelowej musi mieć **odczytu** i **zapisu** uprawnienia do plików źródłowych obrazu w lokacji źródłowej lokalizacji zestawu Windows AIK.  

    -   Podczas migracji pakietu instalacji systemu operacyjnego, upewnij się, że konfiguracja pakietu lokacji źródłowej wskazuje folder zawierający plik WIM, a nie sam plik WIM. Jeżeli pakiet instalacji wskazuje plik WIM, migracja pakietu instalacji nie powiedzie się.  

    -   Podczas migracji pakietu obrazu rozruchowego z lokacji źródłowej programu Configuration Manager 2007, identyfikator pakietu ID nie jest zachowywany w lokacji docelowej. Z tego powodu klienci w hierarchii docelowej nie mogą użyć pakietów obrazu rozruchowego dostępnych we współużytkowanych punktach dystrybucji.  

-   Sekwencje zadań. Podczas migracji sekwencji zadań, która zawiera odwołanie do pakietu instalacyjnego klienta tego odwołania jest zastępowany odwołanie do pakietu instalacyjnego klienta w hierarchii docelowej.  

    > [!NOTE]  
    >  Podczas migracji sekwencji zadań programu Configuration Manager może migrować obiekty, które nie są wymagane w hierarchii docelowej. Te obiekty obejmują obrazy rozruchowe i pakiety instalacyjne klienta programu Configuration Manager 2007.  

-   Sterowniki i pakiety sterowników. Podczas migracji pakietów sterowników, konto komputera dostawcy programu SMS w hierarchii docelowej musi mieć pełną kontrolę do źródła pakietu.

##  <a name="Plan_Migrate_Compliance_settings"></a> Planowanie migracji zarządzania wymaganą konfiguracją  
Można migrować elementy konfiguracji i linie bazowe konfiguracji.  

> [!NOTE]  
>  Niezinterpretowane elementy konfiguracji z hierarchii źródłowej programu Configuration Manager 2007 nie są obsługiwane przez migrację. Nie można migrować ani importować tych elementów konfiguracji do hierarchii docelowej. Aby uzyskać więcej informacji o niezinterpretowanych elementów konfiguracji, zobacz Niezinterpretowane elementy konfiguracji w [About Configuration Items in Desired Configuration Management](http://go.microsoft.com/fwlink/?LinkId=103846) w bibliotece dokumentacji programu Configuration Manager 2007.  

Można importować pakiety konfiguracyjne programu Configuration Manager 2007. Proces importowania powoduje automatyczną konwersję pakiety konfiguracyjne, aby był zgodny z System Center Configuration Manager.  

##  <a name="Plan_migrate_Boundaries"></a> Planowanie migracji granic  
 Granice można migrować między hierarchiami. Podczas migracji z programu Configuration Manager 2007, wszystkie granice z lokacji źródłowej są migrowane jednocześnie oraz dodawane do nowej grupy granic utworzonej w hierarchii docelowej. Podczas migracji z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager, wszystkie granice, którą wybierzesz jest dodawany do nowej grupy granic w hierarchii docelowej.  

 Każda automatycznie utworzona grupa granic może być lokalizacją zawartości, jednak nie może być używana do przypisywania lokacji. Zapobiega to nakładaniu się granic podczas przypisywania lokacji między hierarchiami źródłową i docelową. W przypadku migracji z lokacji źródłowej programu Configuration Manager 2007, to zapobiega nowych klientów programu Configuration Manager 2007, które zainstalować nieprawidłowemu przypisywaniu do hierarchii docelowej. Domyślnie klienci programu System Center Configuration Manager nie są automatycznie przypisywani do lokacji programu Configuration Manager 2007.  

 Podczas migracji, jeśli współużytkujesz punkt dystrybucji z hierarchią docelową, wszystkie granice skojarzone z tą dystrybucją automatycznie migrują do hierarchii docelowej. W hierarchii docelowej proces migracji tworzy nową grupę granic tylko do odczytu dla każdego współużytkowanego punktu dystrybucji. Jeśli zmienisz granice punktu dystrybucji w hierarchii źródłowej, grupa granic w hierarchii docelowej zostanie zaktualizowana tymi zmianami podczas następnego cyklu zbierania danych.  

##  <a name="Plan_Migrate_reports"></a> Planowanie migracji raportów  
Menedżer konfiguracji nie obsługuje migracji raportów. W tej sytuacji raporty można eksportować z hierarchii źródłowej za pomocą narzędzia SQL Server Reporting Services Report Builder, a następnie zaimportować je do hierarchii docelowej.  

> [!NOTE]  
>  Ponieważ istnieją zmiany schematu dla między wersjami programu Configuration Manager 2007 i System Center Configuration Manager, należy sprawdzić każdy raport zaimportowany z hierarchii programu Configuration Manager 2007, aby upewnić się, że działa zgodnie z oczekiwaniami.  

Aby uzyskać więcej informacji o raportach zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="Plan_Migrate_Org_Folders"></a> Planowanie migracji folderów wyszukiwania i organizacyjnych  
 Foldery organizacyjne i folder wyszukiwania można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej. Dodatkowo z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, kryteria dla zapisanego wyszukiwania można migrować do hierarchii docelowej.  

 Domyślnie proces migracji obsługuje obiekty i kolekcje ze struktur folderu wyszukiwania i folderu organizacyjnego. Jednak w kreatorze tworzenia zadania migracji na **ustawienia** strony, można skonfigurować zadania migracji, aby nie migrowało organizacyjnej struktury obiektów, usuwając zaznaczenie pola wyboru pole dla tej opcji. Struktury organizacyjne kolekcji są zawsze obsługiwane.  

 Jedynym wyjątkiem jest folder wyszukiwania, który zawiera aplikacje wirtualne. Podczas migrowania pakietu App-V pakietu App-V jest on przekształcany w aplikację w programie System Center Configuration Manager. Po przeprowadzeniu migracji folderu wyszukiwania zostaną znalezione tylko pozostałe pakiety, a folder wyszukiwania nie może zlokalizować pakietu App-V z powodu konwersji do aplikacji, podczas migracji pakietu aplikacji App-V.  

 Podczas migracji zapisanego kryterium wyszukiwania z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager, można migrować kryteria wyszukiwania, a nie informacje o wynikach wyszukiwania. Migracja zapisanego kryterium wyszukiwania nie ma zastosowania z lokacji źródłowej programu Configuration Manager 2007.  

##  <a name="Plan_Migrate_AI"></a> Planowanie migracji dostosowań analizy zasobów  
 Dostosowania analizy zasobów można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej. Nie wprowadzono żadnych ważnych zmian w strukturze dostosowań analizy zasobów między programu Configuration Manager 2007 i System Center Configuration Manager.  

> [!NOTE]  
>  System Center Configuration Manager nie obsługuje migracji obiektów analizy zasobów z lokacji programu Configuration Manager 2007, która jest używa usługi w wersji 2.0 (AIS 2.0).  

##  <a name="Plan_Migrate_SWM_Rules"></a> Planowanie migracji dostosowań reguł pomiaru użytkowania oprogramowania  
 Nie wprowadzono żadnych ważnych zmian dotyczących pomiaru użytkowania oprogramowania między programu Configuration Manager 2007 i System Center Configuration Manager. Zasady pomiaru użytkowania oprogramowania można migrować z obsługiwanej hierarchii źródłowej do hierarchii docelowej.  

 Domyślnie zasady pomiaru użytkowania oprogramowania, które można migrować do hierarchii docelowej, nie są skojarzone z konkretną lokacją w hierarchii docelowej, lecz mają zastosowanie do wszystkich klientów w hierarchii. Aby zastosować zasadę pomiaru użytkowania oprogramowania do klientów w konkretnej lokacji, należy edytować zasadę pomiaru po jej zmigrowaniu.  
