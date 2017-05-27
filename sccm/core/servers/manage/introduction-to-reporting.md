---
title: Wprowadzenie do raportowania | Dokumentacja firmy Microsoft
description: "Więcej informacji o zestawie narzędzi i zasobów dostępnych do zarządzania raportowania w programie Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 230be984-d2cd-4d53-bd7a-bc24dd93fc22
caps.latest.revision: 7
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 5846ca3c91626491b03b36dd17b454bb9382a8dc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-reporting-in-system-center-configuration-manager"></a>Wprowadzenie do raportowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Raportowanie w programie System Center Configuration Manager udostępnia zestaw narzędzi i zasobów, które ułatwiają korzystanie z zaawansowanych możliwości raportowania programu SQL Server Reporting Services (SSRS) i tworzenia zapewniająca Reporting Services Report Builder. Raportowania pozwala gromadzić, organizować i prezentować informacje o użytkownikach, sprzętu i spisu oprogramowania, aktualizacje oprogramowania, aplikacje, stanie lokacji i innych operacji programu Configuration Manager w organizacji. W ramach raportowania jest dostępnych wiele wstępnie zdefiniowanych raportów, których można użyć bez wprowadzania zmian lub zmodyfikować je, aby spełniały określone wymagania. Ponadto istnieje możliwość tworzenia raportów niestandardowych. Poniższe sekcje służą do zarządzania raportowaniem w programie Configuration Manager.  

##  <a name="BKMK_SQLServerReportingServices"></a> SQL Server Reporting Services  
 Usługi SQL Server Reporting Services zapewniają pełną gamę gotowych do użycia narzędzi i usług ułatwiających tworzenie, wdrażanie oraz zarządzanie raportami w organizacji, a także funkcje programowania, które umożliwiają rozszerzenie i dostosowanie funkcji raportowania. Reporting Services to platforma raportowania oparta na serwerze obejmująca kompleksowe funkcje raportowania w zakresie różnych źródeł danych.  

 Program Configuration Manager używa programu SQL Server Reporting Services stanowią rozwiązanie do raportowania. Integracja z usługami Reporting Services zapewnia następujące korzyści:  

-   Standardowy system raportowania branży używa do zapytania w bazie danych programu Configuration Manager.  

-   Umożliwia wyświetlanie raportów przy użyciu przeglądarki raportów programu Configuration Manager lub za pomocą Menedżera raportów, która jest oparta na sieci web połączenie z raportem.  

-   Zapewnia wysoką wydajność, dostępność i skalowalność.  

-   Umożliwia użytkownikom subskrybowanie raportów; dzięki temu menedżer może na przykład codziennie automatycznie otrzymywać na pocztę e-mail raport zawierający szczegółowe informacje o stanie wdrażania aktualizacji oprogramowania.  

-   Umożliwia eksportowanie raportów dostępnych dla użytkowników w różnych popularnych formatach.  

 Więcej informacji o usługach Reporting Services znajduje się w temacie [SQL Server Reporting Services](http://go.microsoft.com/fwlink/p/?LinkID=212032) w dokumentacji SQL Server 2008 — książki online.  

##  <a name="BKMK_ReportingServicesPoint"></a> Punkt usług raportowania  
 Punkt usług raportowania to rola systemu lokacji zainstalowana na serwerze z uruchomionymi usługami Microsoft SQL Server Reporting Services. Usługi reporting services punktu kopii programu Configuration Manager raport definicje w usługach Reporting Services, tworzy foldery raportów na podstawie raportu kategorii i konfiguruje zasady zabezpieczeń w folderach oraz raportach na podstawie uprawnień opartych na rolach użytkowników administracyjnych programu Configuration Manager. Punkt usług raportowania co 10 minut łączy się z usługami Reporting Services, aby ponownie zastosować zasady zabezpieczeń w przypadku ich zmiany na przykład za pomocą menedżera raportów. Więcej informacji o sposobie planowania i instalowania punktu usług raportowania znajduje się w następującej dokumentacji:  

-   [Planowanie raportowania w programie System Center Configuration Manager](planning-for-reporting.md)  

-   [Konfigurowanie raportowania w programie System Center Configuration Manager](configuring-reporting.md)  

##  <a name="BKMK_ConfigurationManagerReports"></a> Raporty programu Configuration Manager  
 Menedżer konfiguracji zawiera definicje ponad 400 raportów w ponad 50 folderach, które są kopiowane do folderu głównego raportów w usługach SQL Server Reporting Services podczas procesu instalacji punktu usług raportowania. Raporty są wyświetlane w konsoli programu Configuration Manager i organizowane w podfolderach według kategorii raportu. Raporty nie są przenoszone w górę lub w dół hierarchii programu Configuration Manager; działają tylko w odniesieniu do bazy danych lokacji, w której zostały utworzone. Jednak ponieważ programu Configuration Manager replikuje dane globalne w całej hierarchii, masz dostęp do informacji w całej hierarchii. Raport po odebraniu danych z bazy danych lokacji uzyskuje dostęp do danych bieżącej lokacji oraz lokacji podrzędnych, a także do danych globalnych każdej lokacji w hierarchii. Podobnie jak inne obiekty programu Configuration Manager użytkownik administracyjny musi mieć odpowiednie uprawnienia do uruchamiania lub modyfikowania raportów. Aby uruchomić raport, użytkownik administracyjny musi mieć uprawnienie **Uruchamianie raportu** w ramach danego obiektu. Aby utworzyć lub zmodyfikować raport, użytkownik administracyjny musi mieć uprawnienie **Modyfikowanie raportu** w ramach danego obiektu.  

###  <a name="BKMK_CreatingReports"></a> Tworzenie i modyfikowanie raportów  
 Program Configuration Manager używa programu Microsoft SQL Server Report Builder jako jedynego narzędzia raportów na podstawie SQL i na podstawie modelu tworzenia i edycji. Podczas tworzenia lub edytowania raportu w konsoli programu Configuration Manager otworzy program Report Builder. Więcej informacji o zarządzaniu raportami znajduje się w temacie [Operacje i obsługa raportowania w programie System Center Configuration Manager](operations-and-maintenance-for-reporting.md).  

###  <a name="BKMK_RunningReports"></a> Uruchamianie raportów  
 Po uruchomieniu raportu w konsoli programu Configuration Manager Report Viewer otwiera i łączy do usług Reporting Services. Po określeniu wymaganych parametrów raportu usługi Reporting Services pobierają dane i wyświetlają wyniki w przeglądarce. Raporty można również uruchamiać, nawiązując połączenie z usługami SQL Services Reporting Services, a następnie ze źródłem danych lokacji.  

###  <a name="BKMK_ReportPrompts"></a> Monity raportów  
 Monit o raport lub parametr raportu w programie Configuration Manager to właściwości, które można skonfigurować podczas tworzenia lub modyfikowania raportu. Monity raportów mają na celu ograniczenie lub określenie danych pobieranych przez raport. Raport może zawierać więcej niż jeden monit pod warunkiem, że ich nazwy są unikatowe i zawierają tylko znaki alfanumeryczne zgodne z zasadami programu SQL Server dotyczącymi identyfikatorów.  

 Po uruchomieniu raportu wyświetla się monit o podanie wartości wymaganego parametru, na podstawie której zostają pobrane dane raportu. Na przykład raport **Informacje dotyczące określonego komputera** pobiera informacje o określonym komputerze i wyświetla użytkownikowi administracyjnemu monit o podanie nazwy komputera. Usługi Reporting Services przekazują określoną wartość do zmiennej zdefiniowanej w instrukcji języka SQL dla raportu.  

###  <a name="BKMK_ReportLinks"></a> Linki raportów  
 Łącza raportów w programie Configuration Manager są używane w raporcie źródłowym umożliwiają zapewnienie użytkownikom administracyjnym łatwy dostęp do dodatkowych danych, takich jak bardziej szczegółowe informacje o poszczególnych elementach raportu źródłowego. Jeżeli raport docelowy wymaga uruchomienia monitów, w raporcie źródłowym musi znajdować się kolumna z odpowiednimi wartościami dla poszczególnych monitów. Należy określić numer kolumny, która zawiera wartość dla danego monitu. Raport zawierający listę odnalezionych ostatnio komputerów można na przykład połączyć z raportem zawierającym listę ostatnich komunikatów odebranych na określonym komputerze. Po utworzenia łącza można określić, aby kolumna 2 raportu źródłowego zawierała nazwy komputerów wymagane w ramach monitu raportu docelowego. Po uruchomieniu raportu źródłowego po lewej stronie każdego wiersza danych pojawią się ikony łączy. W wyniku kliknięcia ikony w wierszu przeglądarka raportów przekazuje wartość w określonej kolumnie tego wiersza jako wartość monitu wymaganą do wyświetlenia raportu docelowego. W raporcie można skonfigurować tylko jedno łącze, które umożliwia połączenie tylko z jednym zasobem docelowym.  

> [!WARNING]  
>  Przeniesienie raportu docelowego do innego folderu raportów spowoduje zmianę lokalizacji tego raportu. Nowa lokalizacja nie zostanie automatycznie zaktualizowana w linku raportu źródłowego, przez co to link nie będzie działał.  

##  <a name="BKMK_ReportFolders"></a> Foldery raportów  
 Foldery raportów w programie System Center Configuration Manager umożliwiają sortowanie i filtrowanie raportów, które są przechowywane w usługach Reporting Services. Foldery raportów przydają się szczególnie, gdy istnieje wiele zarządzanych raportów. Po zainstalowaniu punktu usług raportowania raporty zostają skopiowane do usług Reporting Services i zorganizowane w ponad 50 folderach raportów. Foldery raportów są przeznaczone wyłącznie do odczytu. Nie można ich modyfikować w konsoli programu Configuration Manager.  

##  <a name="BKMK_ReportSubscriptions"></a> Subskrypcje raportów  
 Subskrypcja raportu w usługach Reporting Services to cykliczne żądanie dostarczenia raportu w określonym czasie lub w odpowiedzi na zdarzenie, w formacie pliku aplikacji określonym w subskrypcji. Subskrypcje są alternatywną metodą uruchamiania raportu na żądanie. W przypadku raportowania na żądanie należy za każdym razem aktywnie wybrać raport do wyświetlenia. Z kolei za pomocą subskrypcji można zaplanować i zautomatyzować proces dostarczania raportu.  

 Subskrypcje raportów w konsoli programu Configuration Manager mogą zarządzać. Przetwarzanie subskrypcji odbywa się na serwerze raportów. Subskrypcje są dystrybuowane przy użyciu rozszerzeń dostarczania wdrożonych na serwerze. Domyślnie można tworzyć subskrypcje w celu wysyłania raportów do folderu udostępnionego lub na adres e-mail. Więcej informacji o zarządzaniu subskrypcjami raportów znajduje się w temacie [Operacje i obsługa raportowania w programie System Center Configuration Manager](operations-and-maintenance-for-reporting.md).  

##  <a name="BKMK_ReportBuilder"></a> Program Program Report Builder  
 Program Configuration Manager używa programu Microsoft SQL Server Reporting Services Report Builder jako jedynego tworzenia i edycji raportów na podstawie SQL i narzędzia zarówno na podstawie modelu. Po zainicjowaniu akcji tworzenia lub edytowania raportu w konsoli programu Configuration Manager otworzy program Report Builder. Program Report Builder jest instalowany automatycznie przy pierwszym utworzeniu lub zmodyfikowaniu raportu. Program Report Builder w wersji skojarzonej z zainstalowaną wersją programu SQL Server jest uruchamiany w przypadku uruchomienia lub edytowania raportów.  

 W ramach instalacji programu Report Builder zostaje włączona obsługa ponad 20 języków. Po uruchomieniu programu Report Builder dane są wyświetlane w języku systemu operacyjnego zainstalowanego na komputerze lokalnym. Jeżeli program Report Builder nie obsługuje danego języka, wyświetla dane w języku angielskim. Program Report Builder obsługuje następujące możliwości dostępne w usługach SQL Server 2008 Reporting Services:  

-   Dostarcza intuicyjne środowisko tworzenia raportów z interfejsem podobnym do pakietu Microsoft Office.  

-   Oferuje elastyczny układ raportu w języku Report Definition Language (RDL) programu SQL Server 2008.  

-   Zapewnia różne formy wizualizacji danych przy użyciu wykresów i mierników.  

-   Zawiera bogato sformatowane pola tekstowe.  

-   Eksportuje raporty do formatu programu Microsoft Word.  

 Program Report Builder można również uruchomić z poziomu usług SQL Server Reporting Services.  

##  <a name="BKMK_ReportModels"></a> Modele raportów w usługach SQL Server Reporting Services  
 Usługi SQL Reporting Services w programie Configuration Manager używa modele raportów ułatwiające użytkownikom administracyjnym wybranie z bazy danych do uwzględnienia w raportach na podstawie modelu elementów. Użytkownik administracyjny tworzący raport może zobaczyć w tych modelach tylko określone widoki i elementy dostępne do wybrania. Do utworzenia raportów na podstawie modelu jest wymagany co najmniej jeden dostępny model. Modele raportów mają następujące funkcje:  

-   Polom i widokom bazy danych można nadać logiczne nazwy firm, aby ułatwić tworzenie raportów. W celu tworzenia raportów nie trzeba znać struktury bazy danych.  

-   Elementy można grupować logicznie.  

-   Istnieje możliwość zdefiniowania relacji między elementami.  

-   Elementy modelu można zabezpieczyć, aby użytkownicy administracyjni mieli dostęp tylko do danych, do których mają uprawnienia.  

 Mimo że program Configuration Manager zawiera przykładowe modele raportów, można również definiować modeli raportów w celu spełnienia wymagań biznesowych. Więcej informacji o sposobie tworzenia modeli raportów znajduje się w temacie [Tworzenie niestandardowych modeli raportów dla programu System Center Configuration Manager w usługach SQL Server Reporting Services](creating-custom-report-models-in-sql-server-reporting-services.md).  

## <a name="next-steps"></a>Następne kroki
[Planowanie raportowania](planning-for-reporting.md)

