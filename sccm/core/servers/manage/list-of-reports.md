---
title: Lista raportów
titleSuffix: Configuration Manager
description: Przejrzyj listę raportów dostępnych w programie Configuration Manager. Należą one do różnych kategorii.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: b7332ed3-8003-454b-bb12-1fdf8721425c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d486907a7819758b27c9a644214ed4d5ec873762
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="list-of-reports-in-system-center-configuration-manager"></a>Lista raportów w programie System Center Configuration Manager.

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Configuration Manager udostępnia wiele wbudowanych raportów, obejmujące wiele zadań raportowania, które można wykonywać. W tych raportach można również używać instrukcji SQL, co pozwoli na tworzenie własnych raportów.   

Następujące raporty są uwzględnione w programie Configuration Manager. Należą one do różnych kategorii.  



## <a name="administrative-security"></a>Zabezpieczenia administracyjne  
 Następujące raporty są wyświetlane w obszarze **zabezpieczenia administracyjne** kategorii.  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Dziennik działań administracyjnych**|Przedstawia rekord zmian administracyjnych wykonanych odnośnie do użytkowników administracyjnych, ról zabezpieczeń, zakresów zabezpieczeń i kolekcje.|  
|**Przydziały zabezpieczeń użytkowników administracyjnych**|Przedstawia dane użytkowników administracyjnych, skojarzone z nimi role zabezpieczeń oraz zakresy zabezpieczeń skojarzone z każdą rolą zabezpieczeń dla każdego użytkownika.|  
|**Obiekty zabezpieczane w ramach pojedynczego zakresu zabezpieczeń**|Wyświetla obiekty, które administrator przypisał do tylko określonego zakresu zabezpieczeń. Ten raport nie wyświetla obiektów, które administrator kojarzy z więcej niż jednego zakresu zabezpieczeń.|  
|**Zabezpieczenia określonych lub wielu obiektów programu Configuration Manager**|Przedstawia obiekty możliwe do zabezpieczenia, zakresy zabezpieczeń skojarzone z obiektami i użytkowników administracyjnych z uprawnieniami do obiektów.|  
|**Podsumowanie ról zabezpieczeń**|Wyświetla role zabezpieczeń i administratorów programu Configuration Manager skojarzonych z poszczególnymi rolami.|  
|**Podsumowanie zakresów zabezpieczeń**|Przedstawia zakresy zabezpieczeń oraz użytkowników administracyjnych programu Configuration Manager i grupy zabezpieczeń skojarzonych z każdym zakresem.|  



## <a name="alerts"></a>Alerty  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Ocena alertu**|Przedstawia podsumowanie wszystkich przełożonych alertów, które zostały wygenerowane między określonymi datami rozpoczęcia i zakończenia.|  
|**Alerty generowane najczęściej**|Przedstawia podsumowanie alertów, które były najczęściej generowane w okresie od określonej daty do daty bieżącej dla określonego obszaru funkcji.|  



## <a name="asset-intelligence"></a>Analiza zasobów  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Sprzęt 01A - podsumowanie komputerów w określonej kolekcji**|Przedstawia widok podsumowania analizy zasobów dla komputerów w określonej kolekcji.|  
|**Sprzęt 03A — użytkownicy podstawowi komputerów**|Przedstawia użytkowników oraz liczbę komputerów, na których dana osoba jest użytkownikiem podstawowym.|  
|**Sprzęt 03B - komputery określonego użytkownika podstawowego konsoli**|Przedstawia wszystkie komputery, dla których określony użytkownik jest użytkownikiem podstawowym konsoli.|  
|**Oprogramowanie 04A - komputery z wieloma użytkownikami (współużytkowane)**|Przedstawia komputery, które nie mają użytkownika podstawowego, ponieważ procent czasu logowania do konsoli dla żadnego z użytkowników nie przekracza 66%.|  
|**Sprzęt 05A - użytkownicy konsoli na określonym komputerze**|Przedstawia wszystkich użytkowników konsoli na określonym komputerze.|  
|**Sprzęt 06A - komputery dla których konsoli nie można ustalić użytkowników**|Pomaga użytkownikom administracyjnym w identyfikowaniu komputerów, na których należy włączyć rejestrowanie zabezpieczeń.|  
|**Sprzęt 07b - urządzenia USB według producenta**|Przedstawia urządzenia USB pogrupowane według producenta.|  
|**Sprzęt 07B - urządzenia USB według producenta i opisu**|Przedstawia urządzenia USB pogrupowane według producenta i opisu.|  
|**Sprzęt 07C - komputery z określonym urządzeniem USB**|Przedstawia wszystkie komputery z określonym urządzeniem USB.|  
|**Sprzęt 07D - urządzenia USB na określonym komputerze**|Przedstawia wszystkie urządzenia USB na określonym komputerze.|  
|**Sprzęt 08A - sprzęt który nie jest gotowy do aktualizacji oprogramowania**|Przedstawia sprzęt, który nie spełnia minimalnych wymagań sprzętowych.|  
|**Sprzęt 09A - wyszukiwanie komputerów**|Wyświetla podsumowanie komputerów spełniających kryteria filtrów słów kluczowych. Te filtry są nazwę komputera, lokacji programu Configuration Manager, domeny, najczęstszego użytkownika konsoli, systemu operacyjnego, producenta lub modelu.|  
|**Sprzęt 10A - komputery w określonej kolekcji które uległy zmianie w określonym przedziale czasu**|Przedstawia listę komputerów w określonej kolekcji, dla których klasa sprzętu została zmieniona w określonym przedziale czasu.|  
|**Sprzęt 10B - zmiany na określonym komputerze w określonym przedziale czasu**|Przedstawia klasy, które zostały zmienione na określonym komputerze w określonym przedziale czasu.|  
|**Licencja 01A - Księga licencji zbiorczych firmy Microsoft dla deklaracje licencyjne firmy Microsoft**|Przedstawia spis wszystkich tytułów oprogramowania firmy Microsoft, które są dostępne w ramach programu licencjonowania zbiorowego firmy Microsoft.|  
|**Licencja 01B — elementy księgi licencji grupowych Microsoft wg kanału sprzedaży**|Identyfikuje i przedstawia kanał sprzedaży dla uwzględnionego w spisie oprogramowania z licencją zbiorczą firmy Microsoft.|  
|**Licencja 01C - komputery z określonym licencjonowania zbiorowego firmy Microsoft księgi elementu i kanałem sprzedaży**|Identyfikuje i przedstawia komputery z określonym elementem księgi licencji zbiorczych firmy Microsoft.|  
|**Licencja 01D - produkty w księdze licencji grupowych Microsoft na określonym komputerze**|Identyfikuje i przedstawia wszystkie elementy księgi licencji zbiorczych firmy Microsoft na określonym komputerze.|  
|**Licencja 02A — liczba licencji wygasną, według przedziałów czasu**|Przedstawia liczbę licencji, które wkrótce wygasną, według określonego przedziału czasu. Wyświetlane produkty licencje są zarządzane przez usługę licencjonowania oprogramowania.|  
|**Licencja 02B - komputery z licencjami bliskimi wygaśnięcia**|Przedstawia określone komputery z licencjami, które wkrótce wygasną.|  
|**Licencja 02C - informacje dotyczące licencji na określonym komputerze**|Przedstawia produkty na określonym komputerze, których licencje są zarządzane przez usługę licencjonowania oprogramowania.|  
|**Licencja 03A - liczba licencji według stanu licencji**|Przedstawia produkty, których licencje są zarządzane przez usługę licencjonowania oprogramowania, uporządkowane według stanu licencji.|  
|**Licencja 03B - komputery z określonym stanem licencji**|Przedstawia produkty, których licencje są zarządzane przez usługę licencjonowania oprogramowania, z określonym stanem licencji.|  
|**Licencja 04A - liczba produktów zarządzanych przez usługę licencjonowania oprogramowania**|Przedstawia liczbę produktów, których licencje są zarządzane przez usługę licencjonowania oprogramowania.|  
|**Licencja 04B - komputery z określonym produktem zarządzanym przez usługę licencjonowania oprogramowania**|Przedstawia komputery zarządzane przez usługę licencjonowania oprogramowania, które zawierają określony produkt.|  
|**Licencja 05A - komputery z usługą zarządzania kluczami**|Przedstawia komputery, które działają jako serwery zarządzania kluczami.|  
|**Licencja 06A - liczba procesorów dla produktów licencjonowanych na procesor**|Przedstawia liczbę procesorów komputerów z produktami firmy Microsoft, które obsługują licencjonowanie w trybie na procesor.|  
|**Licencja 06B — komputery z określonym produktem obsługującym licencję w trybie na procesor**|Przedstawia listę komputerów, na których zainstalowano określony produkt firmy Microsoft obsługujący licencjonowanie w trybie na procesor.|  
|**Licencja 14A - raport dotyczący uzgodnienia programu licencjonowania zbiorowego firmy Microsoft**|Przedstawia uzgodnienia związane z licencjami oprogramowania zakupionymi za pośrednictwem umowy licencjonowania zbiorowego firmy Microsoft oraz rzeczywistą liczbę ze spisu.|  
|**Licencja 14B - listy nie można odnaleźć w MVLS spisu oprogramowania firmy Microsoft**|Ten raport przedstawia tytuły oprogramowania firmy Microsoft w użyciu, których nie znaleziono w umowie licencji zbiorowych firmy Microsoft.|  
|**Licencja 15A - raport uzgadniania ogólnych licencji**|Przedstawia uzgadnianie dotyczące zakupionych ogólnych licencji oprogramowania oraz rzeczywistą liczbę ze spisu.|  
|**Licencja 15B - ogólny raport uzgadniania licencji według komputera**|Przedstawia komputery, na których zainstalowano licencjonowany produkt w określonej wersji.|  
|**Oprogramowanie 01A - podsumowanie zainstalowanego oprogramowania w określonej kolekcji**|Przedstawia podsumowanie zainstalowanego oprogramowania uporządkowane według liczby wystąpień w spisie.|  
|**Oprogramowanie 02A - rodziny produktów dla określonej kolekcji**|Przedstawia rodziny produktów i liczbę programów w rodzinie dla określonej kolekcji.|  
|**Oprogramowanie 02B - kategorie produktów w określonej rodzinie produktów**|Przedstawia kategorie produktów w określonej rodzinie produktów oraz liczbę programów w kategorii.|  
|**Oprogramowanie 02C - oprogramowanie w określonej rodzinie i kategorii produktów**|Przedstawia wszystkie programy, które należą do określonej kategorii i rodziny produktów.|  
|**Oprogramowanie 02D - komputery z zainstalowanym określonym oprogramowaniem**|Przedstawia wszystkie komputery, na których zainstalowano określone oprogramowanie.|  
|**Oprogramowanie 02E - oprogramowanie zainstalowane na określonym komputerze**|Przedstawia wszystkie programy zainstalowane na określonym komputerze.|  
|**Oprogramowanie 03A — oprogramowanie bez kategorii**|Przedstawia oprogramowanie skategoryzowane jako nieznane lub nienależące do żadnej kategorii.|  
|**Oprogramowanie 04A - oprogramowanie skonfigurowane do automatycznego uruchamiania na komputerach**|Przedstawia listę programów skonfigurowanych do automatycznego uruchamiania na komputerach.|  
|**Oprogramowanie 04B - komputery z określonym oprogramowaniem skonfigurowanym do automatycznego uruchamiania**|Przedstawia wszystkie komputery z określonym oprogramowaniem skonfigurowanym do automatycznego uruchamiania.|  
|**Oprogramowanie 04C - oprogramowanie skonfigurowane do automatycznego uruchamiania na określonym komputerze**|Przedstawia zainstalowane oprogramowanie skonfigurowane do automatycznego uruchamiania na określonym komputerze.|  
|**Oprogramowanie 05A - obiekty Pomocnik przeglądarki**|Wyświetla obiekty Pomocnik przeglądarki zainstalowane na komputerach w określonej kolekcji.|  
|**Oprogramowanie 05B - komputery z określonym obiektem Pomocnik przeglądarki**|Wyświetla wszystkie komputery z obiektem pomocniczym przeglądarki określony.|  
|**Oprogramowanie 05C - obiekty Pomocnik przeglądarki na określonym komputerze**|Wyświetla wszystkie obiekty Pomocnik przeglądarki na określonym komputerze.|  
|**Oprogramowanie 06A - wyszukiwanie zainstalowanego oprogramowania**|Ten raport zawiera podsumowanie zainstalowanego oprogramowania. Go wyszukiwania na podstawie następujących kryteriów: Nazwa produktu, wydawcy lub wersji.|  
|**Oprogramowanie 06B - oprogramowanie według nazwy produktu**|Wyświetla podsumowanie oprogramowania zainstalowanego na podstawie nazwy określonego produktu.|  
|**Oprogramowanie 07A - ostatnio używane programy wykonywalne według liczby komputerów**|Przedstawia programy wykonywalne ostatnio używane użytkowników. Zawiera również liczbę komputerów, na których program używany użytkowników. Aby wyświetlanie tego raportu było możliwe, w tej lokacji należy włączyć pomiar użytkowania oprogramowania.|  
|**Oprogramowanie 07B — komputery których ostatnio używany określony program wykonywalny**|Wyświetla listę komputerów, na których użytkownicy ostatnio używali określonego programu wykonywalnego. Ten raport wymaga, aby włączyć ustawienia klienta zliczania oprogramowania.|  
|**Oprogramowanie 07C - ostatnio używane programy wykonywalne na określonym komputerze**|Przedstawia pliki wykonywalne, które użytkownicy ostatnio używane na określonym komputerze. Ten raport wymaga, aby włączyć ustawienia klienta zliczania oprogramowania.|  
|**Oprogramowanie 08A - ostatnio używane programy wykonywalne według liczby użytkowników**|Przedstawia programy wykonywalne ostatnio używane użytkowników. Zawiera również liczbę użytkowników, którzy ostatnio używane program. Ten raport wymaga, aby włączyć ustawienia klienta zliczania oprogramowania.|  
|**Oprogramowanie 08B - użytkownicy którzy używali ostatnio określonego programu wykonywalnego**|Wyświetla użytkowników, którzy ostatnio używali określonego programu wykonywalnego. Ten raport wymaga, aby włączyć ustawienia klienta zliczania oprogramowania.|  
|**Oprogramowanie 08C - ostatnio używane programy wykonywalne według określonego użytkownika**|Przedstawia programy wykonywalne ostatnio używane określonego użytkownika. Ten raport wymaga, aby włączyć ustawienia klienta zliczania oprogramowania.|  
|**Oprogramowanie 09A - rzadko używane oprogramowanie**|Wyświetla listę tytułów oprogramowania bez użycia użytkowników w określonym okresie czasu.|  
|**Oprogramowanie 09B - komputery z rzadko używanym oprogramowaniem**|Wyświetla komputery, na których zainstalowane oprogramowanie, które użytkownicy nie były używane w określonym okresie czasu. Określony przedział czasu opiera się na wartości podanej w raporcie „Oprogramowanie 09A — rzadko używane oprogramowanie”.|  
|**Oprogramowane 10A - tytuły oprogramowania z określonymi zdefiniowanymi wieloma etykietami niestandardowymi**|Przedstawia tytuły oprogramowania w oparciu o dopasowanie wszystkich określonych kryteriów etykiet niestandardowych. Aby zawęzić wyniki wyszukiwania tytułu oprogramowania, można wybrać maksymalnie trzy etykiety niestandardowe.|  
|**Oprogramowanie 10B - komputery z zainstalowanym tytułem oprogramowania z etykietą niestandardową określonych**|Przedstawia wszystkie komputery w tej kolekcji, na których zainstalowano tytuł oprogramowania z określoną etykietą niestandardową.|  
|**Oprogramowanie 11A - tytuły oprogramowania ze zdefiniowaną określoną etykietą niestandardową**|Przedstawia tytuły oprogramowania w oparciu o dopasowanie co najmniej jednego określonego kryterium etykiet niestandardowych.|  
|**Oprogramowanie 12A - tytuły oprogramowania bez etykiety niestandardowej**|Przedstawia wszystkie tytuły oprogramowania, które nie mają zdefiniowanej etykiety niestandardowej.|  
|**Oprogramowanie 14A - Search for tagiem identyfikacji oprogramowania z włączonym**|Przedstawia liczbę zainstalowanych programów z włączonym znacznikiem identyfikacji programu.|  
|**Oprogramowanie 14B - komputery z określonym znacznikiem identyfikacji włączonym zainstalowanego oprogramowania**|Przedstawia wszystkie komputery, na których zainstalowano oprogramowanie z włączonym znacznikiem identyfikacji programu.|  
|**Oprogramowanie 14C - identyfikator tagu włączone oprogramowanie zainstalowane na określonym komputerze**|Przedstawia wszystkie programy z określonym włączonym znacznikiem identyfikacji programu, które zainstalowano na określonym komputerze.|  



## <a name="client-push"></a>Wypychane przez klienta  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Szczegóły stanu instalacji wypychanych klienta**|Przedstawia informacje na temat procesu wypychanej instalacji klienta dla wszystkich lokacji.|  
|**Szczegóły stanu instalacji wypychanych klienta dla określonej lokacji**|Przedstawia informacje na temat procesu wypychanej instalacji klienta dla określonej lokacji.|  
|**Podsumowanie stanu instalacji wypychanych klienta**|Przedstawia widok podsumowania stanu wypychanej instalacji klienta dla wszystkich lokacji.|  
|**Podsumowanie dla określonej lokacji stanu instalacji wypychanych klienta**|Przedstawia widok podsumowania stanu wypychanej instalacji klienta dla określonej lokacji.|  



## <a name="client-status"></a>Stan klienta  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Szczegóły korygowania klienta**|Przedstawia szczegóły akcji korygowania klienta dla określonej kolekcji.|  
|**Podsumowanie korygowania klienta**|Przedstawia podsumowanie akcji korygowania klienta dla określonej kolekcji.|  
|**Historia stanu klienta**|Przedstawia widok historycznych danych dotyczących ogólnego stanu klienta w lokacji.|  
|**Podsumowanie stanu klienta**|Przedstawia wyniki sprawdzania aktywnych klientów dla danej kolekcji.|  
|**Czas klienta na zażądanie zasady**|Wyświetla odsetek klientów, którzy zażądali zasady przynajmniej raz w ciągu ostatnich 30 dni. Każdy dzień reprezentuje odsetek łącznej liczby klientów, którzy zażądali zasady od pierwszego dnia cyklu.|  
|**Klienci w których nie powiodło się sprawdzenie szczegółów**|Przedstawia szczegółowe informacje dotyczące klientów, dla których wystąpiły błędy sprawdzania klienta dla określonej kolekcji.|  
|**Szczegóły nieaktywnych klientów**|Przedstawia szczegółową listę nieaktywnych klientów dla danej kolekcji.|  



## <a name="company-resource-access"></a>Dostęp do zasobów firmy  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Historia wystawiania certyfikatów**|Wyświetla historię certyfikatów wystawionych przez punkt rejestracji certyfikatów dla użytkowników i urządzeń w określonym zakresie dat.|  
|**Lista zasobów według stanu wystawienia certyfikatu**|Przedstawia urządzenia lub użytkowników w określonym stanie wystawiania certyfikatu po dokonaniu oceny określonego profilu certyfikatu.|  
|**Lista zasobów z certyfikatami bliskimi wygaśnięcia**|Przedstawia urządzenia lub użytkowników z certyfikatami wygasającymi w określonym dniu lub wcześniej.|  



## <a name="compliance-and-settings-management"></a>Zarządzanie zgodnością i ustawieniami  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Historia zgodności linii bazowej konfiguracji**|Wyświetla historię zmian zgodności linii bazowej konfiguracji dla określonego przedziału dat.|  
|**Historia zgodności elementu konfiguracji**|Przedstawia historię zmian zgodności elementu konfiguracji dla określonego przedziału dat.|  
|**Zgodność z dostępem warunkowym dla użytkownika**|Wyświetla szczegółowe zgodność z dostępem warunkowym dla określonego użytkownika.|
|**Raport zgodności z dostępem warunkowym**|Raport dotyczący zgodności dostępu warunkowego dla poszczególnych docelowych zasad zgodności.|
|**Szczegóły zgodnych reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Wyświetla informacje o regułach ocenione jako zgodne dla określonego elementu konfiguracji określonego urządzenia lub użytkownika.|  
|**Szczegóły będących w konflikcie reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Wyświetla informacje dotyczące reguł w elemencie konfiguracji wdrożonym, które powodują konflikt z innymi regułami. Inne zasady mogą być zawarte w tym samym lub innym wdrożyć element konfiguracji.|  
|**Szczegóły błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o błędach wygenerowanych przez określony element konfiguracji dla określonego urządzenia lub użytkownika.|  
|**Szczegóły niezgodnych reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o regułach, które zostały ocenione jako niezgodne dla określonego elementu konfiguracji oraz dla określonego urządzenia lub użytkownika.|  
|**Szczegóły skorygowanych reguł elementów konfiguracji w linii bazowej konfiguracji dla zasobu**|Przedstawia informacje o regułach skorygowanych przez określony element konfiguracji dla określonego urządzenia lub użytkownika.|  
|**Lista zasobów według stanu zgodności dla linii bazowej konfiguracji**|Wyświetla urządzeń lub użytkowników z określonym stanem zgodności po ocenie określonej linii bazowej konfiguracji.|  
|**Lista zasobów według stanu zgodności elementu konfiguracji w linii bazowej konfiguracji**|Przedstawia urządzenia lub użytkowników w określonym stanie zgodności po dokonaniu oceny określonego elementu konfiguracji.|  
|**Lista niezgodnych aplikacji i urządzeń dla określonego użytkownika**|Zawiera informacje o użytkownikach i urządzeniach z zainstalowanymi aplikacjami niezgodnymi z wybranymi zasadami.|  
|**Lista reguł w konflikcie z określoną regułą zasobu**|Wyświetla listę reguł w konflikcie z określoną regułą elementu konfiguracji wdrożonego.|  
|**Lista nieznanych zasobów linii bazowej konfiguracji**|Wyświetla listę urządzeń lub użytkowników, którzy nie zaraportowali danych zgodności dotyczących określonej linii bazowej konfiguracji.|  
|**Lista nieznanych zasobów pozycji bazowej konfiguracji**|Przedstawia listę urządzeń lub użytkowników, którzy nie zgłosili jeszcze żadnych danych zgodności dla określonego elementu konfiguracji.|  
|**Reguł i błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu podsumowania**|Wyświetla podsumowanie stanu zgodności reguł oraz wszelkie błędy ustawień określonego elementu konfiguracji. Należy wdrożyć element konfiguracji urządzenia lub użytkownika.|  
|**Podsumowanie zgodności według linii bazowej konfiguracji**|Wyświetla podsumowanie ogólnej zgodności wdrożonych linii bazowych konfiguracji w hierarchii.|  
|**Podsumowanie zgodności według elementów konfiguracji dla linii bazowej konfiguracji**|Wyświetla podsumowanie zgodności elementów konfiguracji w określonej linii bazowej konfiguracji.|  
|**Podsumowanie zgodności według zasad konfiguracji**|Przedstawia podsumowanie zgodności zasad konfiguracji.|  
|**Podsumowanie zgodności linii bazowej konfiguracji dla kolekcji**|Wyświetla podsumowanie ogólnej zgodności określonej linii bazowej konfiguracji. Element konfiguracji, należy wdrożyć w określonej kolekcji.|  
|**Podsumowanie użytkowników z niezgodnymi aplikacjami**|Zawiera informacje o użytkownikach z zainstalowanymi aplikacjami niezgodnymi z wybranymi zasadami.|  
|**Akceptacja warunków i postanowień**|Zawiera elementy warunków i postanowień oraz ich wersje zaakceptowane przez każdego użytkownika.|  



## <a name="device-management"></a>Zarządzanie urządzeniami  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie urządzenia przenośne należące do firmy**|Wyświetla wszystkie firmowej prywatnych urządzeń przenośnych.|
|**Wszyscy klienci urządzeń przenośnych**|Przedstawia informacje o wszystkich klientach urządzeń przenośnych. Urządzenia zarządzane przez łącznik serwera programu Exchange nie są uwzględniane.|  
|**Problemy z certyfikatami na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE, które nie są w dobrej kondycji**|Wyświetla szczegółowe informacje dotyczące problemów z certyfikatami na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Niepowodzenie wdrożenia klienta dla urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla szczegółowe informacje dotyczące niepowodzenia wdrożenia na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Szczegóły stanu wdrażania klienta dla urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla informacje o stanie urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Powodzenie wdrożenia klienta dla urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla szczegółowe informacje dotyczące powodzenia wdrożenia na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Problemy z komunikacją na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE, które nie są w dobrej kondycji**|Ten raport zawiera szczegółowe informacje dotyczące problemów z komunikacją na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Stan zgodności lub domyślne zasady skrzynek pocztowych ActiveSync dla urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange**|Wyświetla podsumowanie stanu zgodności z regułą domyślnego protokołu Exchange ActiveSync dla urządzeń przenośnych zarządzanych przez łącznik serwera Exchange.|  
|**Liczba urządzeń przenośnych według ustawień wyświetlania**|Przedstawia liczbę urządzeń przenośnych według ustawień wyświetlania.|  
|**Liczba urządzeń przenośnych według systemu operacyjnego**|Przedstawia liczbę urządzeń przenośnych według systemu operacyjnego.|  
|**Liczba urządzeń przenośnych według pamięci programu**|Przedstawia liczbę urządzeń przenośnych według pamięci programu.|  
|**Liczba urządzeń przenośnych według konfiguracji pamięci magazynu**|Liczba urządzeń przenośnych według konfiguracji pamięci magazynu|  
|**Informacje o kondycji urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla szczegółowe informacje o kondycji urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Podsumowanie kondycji urządzeń przenośnych, zarządzanych przez klienta programu Configuration Manager dla systemu Windows CE**|Wyświetla informacje podsumowania kondycji urządzeń przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Nieaktywne urządzenia przenośne, które są zarządzane przez łącznik serwera Exchange**|Przedstawia urządzenia przenośne zarządzane przez łącznik serwera Exchange, które nie nawiązywały połączenia z serwerem Exchange Server w ciągu określonej liczby dni.|  
|**Lista urządzeń uporządkowana według stanu dostępu warunkowego**|Zawiera informacje o bieżącym stanie zgodności i dostępu warunkowego urządzeń. Tego raportu można używać z zasadami dostępu warunkowego. Ten raport jest dostępny od wersji 1602 programu Configuration Manager.|  
|**Lista urządzeń uporządkowana według stanu zaświadczania o kondycji**|Wyświetla listę urządzeń z atrybutami zgłoszonymi przez usługę zaświadczania o kondycji|
|**Lista urządzeń zarejestrowanych przez użytkownika w programie Microsoft Intune**|Wyświetla wszystkie urządzenia, które użytkownik zarejestrował w usłudze Microsoft Intune.|  
|**Lista urządzeń w konkretnej kategorii urządzeń**|Wyświetla informacje o wszystkich urządzeniach w konkretnej kategorii urządzeń.|
|**Problemy z klientami lokalnymi na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE, które nie są w dobrej kondycji**|Ten raport zawiera szczegółowe informacje na temat problemów z klientami lokalnymi na urządzeniach przenośnych, które są zarządzane przez klienta programu Configuration Manager dla systemu Windows CE.|  
|**Informacje o kliencie urządzenia przenośnego**|Wyświetla informacje o urządzeniach przenośnych, które mają zainstalowanego klienta programu Configuration Manager. Z tego raportu można skorzystać, aby sprawdzić, które urządzenia przenośne mogą się pomyślnie komunikować z punktem zarządzania.|  
|**Szczegóły zgodności urządzeń przenośnych dotyczące łącznika serwera Exchange**|Przedstawia szczegóły zgodności urządzenia przenośnego dla domyślnych zasad skrzynki pocztowej programu Exchange ActiveSync, które zostały skonfigurowane przy użyciu łącznika serwera programu Exchange.|  
|**Urządzenia przenośne według systemu operacyjnego**|Przedstawia urządzenia przenośne według systemu operacyjnego.|  
|**Urządzenia przenośne ze złamanymi ograniczeniami lub z odblokowanym**|Przedstawia urządzenia przenośne ze złamanymi ograniczeniami lub z odblokowanym dostępem.|  
|**Urządzenia przenośne, które nie są zarządzane ponieważ mimo zarejestrowania nie zostały przypisane do lokacji**|Przedstawia urządzenia przenośne, które ukończyły rejestrację w programie Configuration Manager ma certyfikat, ale nie można ukończyć przypisywanie lokacji.|  
|**Urządzenia przenośne z określoną ilością wolnej pamięci programu**|Przedstawia wszystkie urządzenia przenośne z określoną ilością wolnej pamięci programu.|  
|**Urządzenia przenośne z określoną ilością wolnej wymiennej pamięci magazynu**|Przedstawia wszystkie urządzenia przenośne z określoną ilością wolnej pamięci magazynu wymiennego.|  
|**Urządzenia przenośne z problemami dotyczącymi odnowienia certyfikatu**|Przedstawia zarejestrowane urządzenia przenośne, którym nie udało się odnowić certyfikatu. Jeśli nie odnowisz certyfikatu przed datą wygaśnięcia, te urządzenia przenośne być zarządzana.|  
|**Urządzenia przenośne z niewielką ilością wolnej pamięci (poniżej wielkości określonej w KB) programu**|Przedstawia urządzenia przenośne, dla których pamięć programu jest mniejsza niż określony rozmiar w KB.|  
|**Urządzenia przenośne z niskim wolnej wymiennej pamięci magazynu (poniżej wielkości określonej w KB)**|Przedstawia urządzenia przenośne, dla których pamięć magazynu wymiennego jest mniejsza niż określony rozmiar w KB.|  
|**Liczba urządzeń zarejestrowanych przez użytkownika w programie Microsoft Intune**|Wyświetla użytkowników włączony dla subskrypcji Microsoft Intune. Ponadto całkowita liczba urządzeń zarejestrowanych dla każdego użytkownika.|  
|**Oczekujące żądania wycofania i czyszczenia dla urządzeń przenośnych**|Przedstawia oczekujące żądania czyszczenia danych dla urządzeń przenośnych.|  
|**Ostatnio zarejestrowane i przypisane urządzenia przenośne**|Przedstawia urządzenia przenośne, które ostatnio zarejestrowane w programie Configuration Manager i przypisane do lokacji.|  
|**Ostatnio wyczyszczone urządzenia przenośne**|Przedstawia listę urządzeń przenośnych, które zostały ostatnio pomyślnie wyczyszczone.|  
|**Ustawienia podsumowania dla urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange**|Wyświetla liczbę urządzeń przenośnych, które są stosowane ustawienia dla każdej zasady skrzynki pocztowej domyślnego protokołu Exchange ActiveSync, zarządzane przez łącznik serwera Exchange.|  
|**Szczegółowy stan kluczy ładowania bezpośredniego systemu Windows RT**|Przedstawia szczegółowe informacje o stanie dla określonego klucza ładowania bezpośredniego w systemie Windows RT.|  
|**Podsumowanie kluczy ładowania bezpośredniego systemu Windows RT**|Przedstawia stan kluczy ładowania bezpośredniego w systemie Windows RT.|  



## <a name="driver-management"></a>Zarządzanie sterownikami  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie sterowniki**|Przedstawia listę wszystkich sterowników.|  
|**Wszystkie sterowniki dla określonej platformy**|Przedstawia wszystkie sterowniki dla określonej platformy.|  
|**Wszystkie sterowniki w określonym obrazie rozruchowym**|Przedstawia wszystkie sterowniki w określonym obrazie rozruchowym.|  
|**Wszystkie sterowniki określonej kategorii**|Przedstawia wszystkie sterowniki w określonej kategorii.|  
|**Wszystkie sterowniki określonego pakietu**|Przedstawia wszystkie sterowniki w określonym pakiecie.|  
|**Kategorie określonego sterownika**|Przedstawia kategorie dla określonego sterownika.|  
|**Komputery, których nie powiodła się instalacja sterowników dla określonej kolekcji**|Przedstawia komputery, na których nie można zainstalować sterowników dla określonej kolekcji.|  
|**Raport dla określonej kolekcji dopasowania katalogu sterowników**|Przedstawia raport dopasowania wykazu sterowników dla określonej kolekcji.|  
|**Raport dla określonego komputera dopasowania katalogu sterowników**|Przedstawia raport dopasowania wykazu sterowników dla określonego komputera.|  
|**Raport dla określonego urządzenia na określonym komputerze dopasowania katalogu sterowników**|Przedstawia raport dopasowania wykazu sterowników dla określonego urządzenia na określonym komputerze.|  
|**Sterownik raport dopasowania wykazu dla komputerów w określonej kolekcji z określonym urządzeniem**|Przedstawia raport dopasowania wykazu sterowników dla komputerów w określonej kolekcji z określonym urządzeniem.|  
|**Sterowniki, których nie można zainstalować na określonym komputerze**|Przedstawia sterowniki, których nie można zainstalować na określonym komputerze.|  
|**Obsługiwane platformy dla określonego sterownika**|Przedstawia obsługiwane platformy dla określonego sterownika.|  



## <a name="endpoint-protection"></a>Program Endpoint Protection  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport aktywności ochrony przed złośliwym oprogramowaniem**|Przedstawia omówienie działania oprogramowania chroniącego przed złośliwym kodem.|  
|**Ogólny stan ochrony przed złośliwym oprogramowaniem i historii**|Przedstawia ogólny stan i historię oprogramowania chroniącego przed złośliwym kodem.|  
|**Szczegóły złośliwego oprogramowania na komputerze**|Przedstawia szczegółowe informacje dotyczące określonego komputera oraz listę zainstalowanego na nim złośliwego oprogramowania.|  
|**Zainfekowane komputery**|Przedstawia listę komputerów, na których wykryto określone zagrożenie.|  
|**Użytkownicy z największą liczbą zagrożeń**|Przedstawia listę użytkowników z największą liczbą wykrytych zagrożeń.|  
|**Lista zagrożeń użytkownika**|Przedstawia listę zagrożeń znalezionych na określonym koncie użytkownika.|  



## <a name="hardware---cd-rom"></a>Sprzęt — CD-ROM  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Informacje o napędach CD-ROM dla określonego komputera**|Przedstawia informacje o napędach CD-ROM na określonym komputerze.|  
|**Komputery dla określonego producenta napędów CD-ROM**|Przedstawia listę komputerów z napędem CD-ROM od określonego producenta.|  
|**Liczba napędów CD-ROM według producentów**|Przedstawia liczbę napędów CD-ROM na producenta uwzględnionych w spisie.|  
|**Historia - Historia napędów CD-ROM dla określonego komputera**|Przedstawia historię spisu napędów CD-ROM na określonym komputerze.|  



## <a name="hardware---disk"></a>Sprzęt — dysk  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z dyskami twardymi określonego rozmiaru**|Przedstawia listę komputerów z dyskami twardymi o określonym rozmiarze.|  
|**Komputery z niewielką ilością wolnego miejsca (mniej niż określony %) na dysku**|Przedstawia listę komputerów w określonej kolekcji, które mają mniej wolnego miejsca na dysku niż określona wartość.|  
|**Komputery z mało wolnego miejsca na dysku (mniejszą niż określona liczba MB)**|Przedstawia listę komputerów i dysków z małą ilością wolnego miejsca. Ilość wolnego miejsca do sprawdzenia jest wyrażona w megabajtach.|  
|**Liczba konfiguracji dysku fizycznego**|Przedstawia liczbę dysków twardych w spisie uporządkowanych według pojemności dysku.|  
|**Informacje o dyskach dla określonego komputera - dyski logiczne**|Przedstawia podsumowanie informacji o dyskach logicznych na określonym komputerze.|  
|**Informacje o dyskach dla określonego komputera - partycje**|Przedstawia podsumowanie informacji o partycjach dysków na określonym komputerze.|  
|**Informacje o dyskach dla określonego komputera - dyski fizyczne**|Przedstawia podsumowanie informacji o dyskach fizycznych na określonym komputerze.|  
|**Historia - Historia miejsca na dyskach logicznych dla określonego komputera**|Przedstawia historię spisu napędów dysków logicznych na określonym komputerze.|  



## <a name="hardware---general"></a>Sprzęt — ogólne  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Informacje dotyczące określonego komputera**|Przedstawia podsumowanie informacji o określonym komputerze.|  
|**Komputery w określonej grupie roboczej lub domenie**|Przedstawia listę komputerów w określonej grupie roboczej lub domenie.|  
|**Klasy spisu przypisane do określonej kolekcji**|Przedstawia klasy spisu przypisane do określonej kolekcji.|  
|**Klasy spisu włączone na określonym komputerze**|Przedstawia klasy spisu włączone na określonym komputerze.|  
|**Informacje o urządzeniu AutoPilot systemu Windows**|Wyświetla informacje o urządzeniu klienta, potrzebnego do rejestracji AutoPilot systemu Windows.|



## <a name="hardware---memory"></a>Sprzęt — pamięć  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery których pamięć fizyczna uległa zmianie**|Przedstawia listę komputerów, na których ilość pamięci RAM zmieniła się od ostatniego cyklu spisu.|  
|**Komputery z określoną ilością pamięci**|Przedstawia listę komputerów, które mają określoną ilość pamięci RAM (całkowita ilość pamięci fizycznej zaokrąglona do najbliższego MB).|  
|**Komputery z niewielką ilością wolnej pamięci (mniejszą lub równą określonej w MB)**|Przedstawia listę komputerów z małą ilością pamięci. Ilość pamięci do sprawdzenia jest wyrażona w megabajtach.|  
|**Liczba konfiguracji pamięci**|Przedstawia liczbę komputerów w spisie uporządkowanych według ilości pamięci RAM.|  
|**Informacje o pamięci dla określonego komputera**|Przedstawia podsumowanie informacji o pamięci na określonym komputerze.|  



## <a name="hardware---modem"></a>Sprzęt — Modem  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery dla określonego producenta modemu**|Przedstawia listę komputerów z modemem oferowanym przez określonego producenta.|  
|**Liczba modemów według producenta**|Przedstawia liczbę modemów w spisie dla każdego producenta modemów.|  
|**Informacje dotyczące modemu dla pojedynczego komputera**|Przedstawia podsumowanie informacji o modemie na określonym komputerze.|  



## <a name="hardware---network-adapter"></a>Sprzęt — karta sieciowa  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą sieciową**|Przedstawia listę komputerów z określoną kartą sieciową.|  
|**Liczba kart sieciowych według typu**|Przedstawia liczbę kart sieciowych w spisie uporządkowanych według typu.|  
|**Informacje dotyczące karty sieciowej dla określonego komputera**|Przedstawia informacje o kartach sieciowych zainstalowanych na określonym komputerze.|  



## <a name="hardware---processor"></a>Sprzęt — procesor  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z procesorem o określonej szybkości**|Przedstawia listę komputerów z procesorem o określonej szybkości.|  
|**Komputery wyposażone w szybkie procesory (większe niż lub równej określonej szybkości zegara)**|Przedstawia listę komputerów z procesorami o szybkości większej niż określona.|  
|**Komputery wyposażone w wolne procesory (o szybkości mniejszej lub równej określonej szybkości zegara)**|Przedstawia listę komputerów z procesorami działającymi z określoną szybkością zegara lub wolniej.|  
|**Liczba szybkości procesora**|Przedstawia liczbę komputerów w spisie uporządkowanych według szybkości procesora.|  
|**Informacje dotyczące procesora dla pojedynczego komputera**|Przedstawia informacje o procesorach zainstalowanych na określonym komputerze.|  



## <a name="hardware---scsi"></a>Sprzęt — SCSI  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą SCSI typem**|Przedstawia listę komputerów z zainstalowaną określoną kartą SCSI.|  
|**Liczba typów kart SCSI**|Przedstawia liczbę kart SCSI w spisie uporządkowanych według typu karty.|  
|**Informacje dotyczące karty SCSI dla pojedynczego komputera**|Przedstawia informacje o kartach SCSI zainstalowanych na określonym komputerze.|  



## <a name="hardware---security"></a>Sprzęt — zabezpieczeń

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Szczegółowe informacje o Państwa oprogramowania układowego na urządzeniach**|Wyświetla szczegółowe informacje o stanach UEFI, funkcji SecureBoot i modułu TPM|  



## <a name="hardware---sound-card"></a>Sprzęt — karta dźwiękowa  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą dźwiękową**|Przedstawia listę komputerów z określoną kartą dźwiękową.|  
|**Liczba kart dźwiękowych**|Przedstawia liczbę komputerów w spisie uporządkowanych według typu karty dźwiękowej.|  
|**Informacje o karty dźwiękowej dla pojedynczego komputera**|Przedstawia podsumowanie informacji o karcie dźwiękowej na określonym komputerze.|  



## <a name="hardware---video-card"></a>Sprzęt — karta wideo  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną kartą graficzną**|Przedstawia listę komputerów z określoną kartą wideo.|  
|**Liczba kart graficznych według typu**|Wyświetla listę wszystkich kart graficznych zainstalowanych na komputerach. Ponadto liczba kart graficznych poszczególnych typów.|  
|**Informacje dotyczące karty graficznej dla pojedynczego komputera**|Przedstawia informacje o kartach wideo zainstalowanych na określonym komputerze.|  



## <a name="migration"></a>Migracja  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Klienci na liście wykluczeń**|Przedstawia klientów wykluczonych z migracji.|  
|**Zależność od kolekcji programu Configuration manager**|Przedstawia obiekty zależne od kolekcji hierarchii źródłowej.|  
|**Właściwości zadania migracji**|Przedstawia zawartość określonego zadania migracji.|  
|**Zadania migracji**|Przedstawia listę zadań migracji.|  
|**Obiekty niezmigrowane**|Przedstawia listę obiektów, dla których ostatnia próba migracji zakończyła się niepowodzeniem.|  



## <a name="network"></a>Sieć  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Liczba adresów IP według podsieci**|Przedstawia liczbę adresów IP w spisie dla każdej podsieci IP.|  
|**IP - wszystkie podsieci według maski podsieci**|Przedstawia listę podsieci i masek podsieci IP.|  
|**IP — komputery w określonej podsieci**|Przedstawia listę komputerów i informacje o adresie IP dla określonej podsieci IP.|  
|**IP - informacje dotyczące określonego komputera**|Przedstawia podsumowanie informacji na temat adresu IP na określonym komputerze.|  
|**IP - informacje dotyczące określonego adresu IP**|Przedstawia podsumowanie informacji na temat określonego adresu IP.|  
|**MAC - komputery z określonym adresem MAC**|Przedstawia nazwę komputera i adres IP dla komputerów z określonym adresem MAC.|  



## <a name="operating-system"></a>System operacyjny  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Historia wersji systemu operacyjnego na komputerze**|Przedstawia historię spisu dla systemu operacyjnego na określonym komputerze.|  
|**Komputery z określonym systemem operacyjnym**|Przedstawia komputery z określonym systemem operacyjnym.|  
|**Komputery z określonym systemem operacyjnym i dodatkiem service pack**|Przedstawia komputery z określonym systemem operacyjnym i dodatkiem Service Pack.|  
|**Liczba wersji systemu operacyjnego**|Przedstawia liczbę komputerów w spisie uporządkowanych według systemu operacyjnego.|  
|**Liczba systemów operacyjnych i dodatków service pack**|Przedstawia liczbę komputerów w spisie uporządkowanych według kombinacji systemu operacyjnego i dodatku Service Pack.|  
|**Usługi - komputery z uruchomioną określoną usługą**|Przedstawia listę komputerów z uruchomioną określoną usługą.|  
|**Usługi - komputery z uruchomionym serwerem dostępu zdalnego**|Przedstawia listę komputerów z uruchomionym serwerem dostępu zdalnego.|  
|**Usługi - informacje dotyczące określonego komputera usług**|Przedstawia podsumowanie informacji o usługach na określonym komputerze.|  
|**Szczegóły obsługi systemu Windows 10 dla określonej kolekcji**|Wyświetlane są ogólne informacje na temat obsługi systemu Windows 10 dla określonej kolekcji.|
|**Komputery z systemem Windows Server**|Przedstawia listę komputerów z systemem operacyjnym Windows Server.|  



## <a name="power-management"></a>Zarządzanie energią  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zarządzanie energią - aktywność komputera**|Wyświetla wykres przedstawiający aktywność monitora, komputera i użytkownika dla określonej kolekcji w określonym przedziale czasu.|  
|**Zarządzanie energią - aktywność komputera według komputera**|Wyświetla wykres przedstawiający aktywność monitora, komputera i użytkownika dla określonego komputera w określonym dniu.|  
|**Zarządzanie energią - szczegóły aktywności komputera**|Przedstawia listę możliwości uśpienia i przebudzenia komputerów w określonej kolekcji w określonym dniu i o określonej godzinie.|  
|**Zarządzanie energią — szczegóły komputera**|Wyświetla szczegółowe informacje dotyczące możliwości zasilania, ustawień zasilania i planów zasilania zastosowanych na określonym komputerze.|  
|**Zarządzanie energią - szczegóły komputerów bez zgłoszeń**|Przedstawia listę komputerów niezgłaszających żadnej aktywności związanej z zasilaniem dla określonej daty i godziny.|  
|**Zarządzanie energią — wykluczone komputery**|Przedstawia listę komputerów wykluczonych z planu zasilania.|  
|**Zarządzanie energią - komputery z wieloma planami zasilania**|Przedstawia listę komputerów, na których zastosowano wiele ustawień zasilania powodujących konflikt.|  
|**Zarządzanie energią - pobór energii**|Przedstawia całkowite miesięczne zużycie energii (w kWh) dla określonej kolekcji w określonym przedziale czasu.|  
|**Zarządzanie energią - pobór energii wg dnia**|Przedstawia całkowite zużycie energii (w kWh) dla określonej kolekcji w ciągu ostatnich 31 dni.|  
|**Zarządzanie energią - koszt energii**|Przedstawia całkowity miesięczny koszt zużycia energii dla określonej kolekcji w określonym przedziale czasu.|  
|**Zarządzanie energią - koszt energii wg dnia**|Przedstawia całkowity koszt zużycia energii dla określonej kolekcji w ciągu ostatnich 31 dni.|  
|**Zarządzanie energią — wpływ na środowisko**|Przedstawia wykres emisji dwutlenku węgla (CO2) generowanego przez określoną kolekcję w określonym przedziale czasu.|  
|**Zarządzanie energią — wpływ na środowisko wg dnia**|Przedstawia wykres emisji dwutlenku węgla (CO2) generowanego przez określoną kolekcję w ciągu ostatnich 31 dni.|  
|**Zarządzanie energią - szczegóły braku usypiania komputera**|Przedstawia szczegółowe informacje dotyczące komputerów, które nie były wprowadzane w stan uśpienia ani hibernacji w określonym przedziale czasu.|  
|**Zarządzanie energią — raport o braku usypiania**|Wyświetla listę częstych przyczyn uniemożliwiających przejście komputerów w stan uśpienia lub hibernacji. Zawiera on również liczbę komputerów, których te przyczyny dotyczyły, w określonym przedziale czasu.|  
|**Zarządzanie energią — możliwości zasilania**|Przedstawia możliwości zarządzania energią dla komputerów w określonej kolekcji.|  
|**Zarządzanie energią — ustawienia zasilania**|Przedstawia zagregowaną listę ustawień zasilania używanych na komputerach w określonej kolekcji.|  
|**Zarządzanie energią - szczegóły ustawień zasilania**|Używane, aby wyświetlić więcej informacji o komputerach, które zostały określone w **zarządzanie energią — ustawienia zasilania** raportu.|  



## <a name="replication-traffic"></a>Ruch związany z replikacją  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Globalny danych replikacji ruchu na jedno łącze (wykres liniowy)**|Przedstawia całkowity ruch związany z replikacją danych globalnych za pomocą określonego linku dla określonej liczby dni.|  
|**Globalny danych replikacji ruchu na jedno łącze (wykres kołowy)**|Przedstawia całkowity ruch związany z replikacją danych globalnych za pomocą określonego linku dla określonej liczby dni.|  
|**Ruch związany z replikacją hierarchii według łącza**|Przedstawia całkowity ruch związany z replikacją dla każdego linku w hierarchii w ciągu określonej liczby dni.|  
|**Hierarchii pierwszych dziesięciu replikacji grupy ruchu na jedno łącze (wykres kołowy)**|Przedstawia ruch związany z replikacją w głównych 10 grupach replikacji w całej hierarchii zidentyfikowanych według łącza.|  
|**Ruch związany z replikacją łącza**|Przedstawia całkowity ruch związany z replikacją dla wszystkich danych w ciągu określonej liczby dni.|  
|**Ruch związany z grupami replikacji na jedno łącze**|Przedstawia ruch sieciowy związany z grupami replikacji dla określonego linku replikacji bazy danych w ciągu określonej liczby dni.|  
|**Witryna danych replikacji ruchu na jedno łącze (wykres liniowy)**|Przedstawia całkowity ruch związany z replikacją danych lokacji za pomocą określonego linku w ciągu określonej liczby dni.|  
|**Witryna danych replikacji ruchu na jedno łącze (wykres kołowy)**|Przedstawia całkowity ruch związany z replikacją danych lokacji za pomocą określonego linku w ciągu określonej liczby dni.|  
|**Całkowita liczba replikacją hierarchii (wykres liniowy)**|Przedstawia replikację zagregowanych danych hierarchii — lokacji i globalnych — w każdym kierunku linku w ciągu określonej liczby dni.|  
|**Całkowita liczba replikacją hierarchii (wykres kołowy)**|Przedstawia replikację zagregowanych danych hierarchii — lokacji i globalnych — w każdym kierunku linku w ciągu określonej liczby dni.|  



## <a name="site---client-information"></a>Lokacja — informacje o kliencie  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport o stanie szczegółowym przypisywania klienta**|Przedstawia szczegółowe informacje na temat stanu przypisywania klientów.|  
|**Szczegóły niepowodzenia przypisywania klienta**|Przedstawia szczegółowe informacje na temat niepowodzeń przypisywania klientów.|  
|**Szczegóły stanu przypisywania klientów**|Przedstawia omówienie stanu przypisywania klientów.|  
|**Szczegóły powodzenia przypisywania klienta**|Przedstawia szczegółowe informacje na temat pomyślnie przypisanych klientów.|  
|**Raport niepowodzeń wdrażania klientów**|Przedstawia szczegółowe informacje na temat klientów, których nie można było wdrożyć.|  
|**Szczegóły stanu wdrożenia klienta**|Przedstawia podsumowanie informacji na temat stanu instalacji klientów.|  
|**Raport powodzeń wdrażania klientów**|Przedstawia szczegółowe informacje na temat klientów, którzy zostali pomyślnie wdrożeni.|  
|**Klienci bez możliwości komunikacji protokołu HTTPS**|Wyświetla szczegółowe informacje dotyczące każdego klienta, który uruchamia narzędzie gotowości komunikacji protokołu HTTPS, a następnie raportuje jako niezdolne do komunikacji za pośrednictwem protokołu HTTPS.|  
|**Komputery przypisane, ale niezainstalowane dla określonej lokacji**|Wyświetla listę komputerów przypisanych do określonej lokacji, ale nieraportujących do tej lokacji.|  
|**Komputery z określoną wersją klienta programu Configuration Manager**|Wyświetla listę komputerów z określoną wersją oprogramowania klienckiego programu Configuration Manager.|  
|**Liczba klientów i protokół używany do komunikacji**|Przedstawia podsumowanie metod komunikacji używanych przez klientów (protokół HTTP lub HTTPS).|  
|**Liczba klientów przypisanych i zainstalowanych dla każdej lokacji**|Przedstawia liczbę komputerów przypisanych i zainstalowanych w każdej lokacji. Klienci z lokalizacją sieciową skojarzoną z wieloma lokacjami są traktowani jako zainstalowani, jeśli ich raportowanie dotyczy tej lokacji.|  
|**Liczba klientów z obsługą komunikacji protokołu HTTPS**|Wyświetla szczegółowe informacje o każdym kliencie uruchomionym narzędziem gotowości komunikacji protokołu HTTPS i raporty do obsługę lub brak obsługi komunikacji za pośrednictwem protokołu HTTPS.|  
|**Liczba klientów dla każdej lokacji**|Wyświetla liczbę klientów programu Configuration Manager zainstalowane według kodu lokacji.|  
|**Klientów liczba programu Configuration Manager według wersji klienta**|Wyświetla liczbę komputerów wykrytych przez wersję klienta programu Configuration Manager.|  
|**Szczegóły problemu raportowanego do punktu stanu powrotu dla określonej kolekcji**|Wyświetla szczegółowe informacje o problemach raportowanych przez klientów w określonej kolekcji. Ci klienci muszą mieć przypisane rezerwowy punkt stanu.|  
|**Szczegóły problemu raportowanego do punktu stanu powrotu dla określonej lokacji**|Wyświetla szczegółowe informacje o problemach raportowanych przez klientów w określonej lokacji. Ci klienci muszą mieć przypisane rezerwowy punkt stanu.|  
|**Podsumowanie problemów raportowanych do punktu stanu powrotu**|Wyświetla informacje o wszystkich problemach raportowanych przez klientów. Ci klienci muszą mieć przypisane rezerwowy punkt stanu.|  
|**Podsumowanie problemów raportowanych do punktu stanu powrotu dla określonej kolekcji**|Wyświetla podsumowanie problemów raportowanych przez klientów w określonej kolekcji. Ci klienci muszą mieć przypisane rezerwowy punkt stanu.|  



## <a name="site---discovery-and-inventory-information"></a>Lokacja — odnajdywania i informacje o spisie  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Klienci, którzy nie zgłosili się ostatnio (w ciągu określonej liczby dni)**|Przedstawia listę klientów, którzy nie raportowali danych odnajdowania, spisu sprzętu ani spisu oprogramowania w ciągu określonej liczby dni.|  
|**Komputery odnalezione przez określoną lokację**|Wyświetla listę wszystkich komputerów, które odnalezione w określonej lokacji. Przedstawia on także datę ostatniego odnajdywania.|  
|**Komputery odnalezione ostatnio według metody odnajdywania**|Wyświetla listę komputerów, które witryny odnalezione w ciągu określonej liczby dni. Zawiera także listę agentów, które dokonały odnalezienia. Jeśli wielu agentów odnaleziony komputer, go może występować więcej niż raz na liście.|  
|**Komputery nieodnalezione ostatnio (w ciągu określonej liczby dni)**|Wyświetla listę komputerów, które lokacji nie ma ostatnio odnalezione. Zawiera również liczbę dni, od lokacji odnalezienia komputera.|  
|**Komputery niespisane ostatnio (w ciągu określonej liczby dni)**|Wyświetla listę komputerów, które nie ma ostatnio spisane lokacji. Przedstawiono również się, że ostatni czas klienta spisu komputera.|  
|**Komputery, które mogą współdzielić sam Unikatowy identyfikator programu Configuration Manager**|Przedstawia listę komputerów, których nazwy zostały zmienione. Zmiana nazwy jest możliwym objawem dwa komputera identyfikatora unikatowego programu Configuration Manager z innego komputera.|  
|**Komputery ze zduplikowanymi adresami MAC**|Przedstawia komputery korzystające z tego samego adresu MAC.|  
|**Liczba komputerów w domenach zasobów lub grupach roboczych**|Przedstawia liczbę komputerów w każdej grupie roboczej lub domenie zasobów.|  
|**Informacje dotyczące odnajdywania określonego komputera**|Przedstawia listę agentów i lokacji, przy użyciu których odnaleziono określony komputer.|  
|**Daty spisu dla określonego komputera**|Przedstawia datę i godzinę ostatniego uruchomienia spisu na określonym komputerze.|  



## <a name="site---general"></a>Lokacja — ogólne  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery w określonej lokacji**|Przedstawia listę komputerów w określonej lokacji.|  
|**Stan lokacji w hierarchii**|Przedstawia listę lokacji w hierarchii oraz informacje na temat wersji i stanu lokacji.|  
|**Stan aktualizacji programu Configuration Manager w hierarchii**|Wyświetla informacje o aktualizacji lokacji programu Configuration Manager w hierarchii.|  



## <a name="site---server-information"></a>Lokacja — informacje o serwerze  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Role systemu lokacji i serwery systemu lokacji dla określonej lokacji**|Przedstawia listę serwerów systemu lokacji i ich ról systemu lokacji dla określonej lokacji.|  



## <a name="software---companies-and-products"></a>Oprogramowanie — firmy i produkty  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie spisane produkty określonego producenta oprogramowania**|Przedstawia listę produktów programowych i ich wersji oferowanych przez określonego producenta oprogramowania.|  
|**Wszyscy producenci oprogramowania**|Przedstawia listę wszystkich firm produkujących oprogramowanie uwzględnione w spisie.|  
|**Wszystkie aplikacje systemu Windows**|Przedstawia podsumowanie zainstalowanych aplikacji systemu Windows. Wyszukuje, używając następujących kryteriów: Nazwa aplikacji, architektury lub wydawcy.|  
|**Komputery z określonym produktem**|Przedstawia listę komputerów, na których znajduje się określony produkt uwzględniony w spisie, wraz z wersją tego produktu.|  
|**Komputery z określonym produktem nazwa i wersja**|Przedstawia listę komputerów, na których znajduje się określona wersja produktu uwzględniona w spisie.|  
|**Komputery z określonym oprogramowaniem zarejestrowanym w aplecie Dodaj Usuń programy**|Przedstawia podsumowanie wszystkich komputerów z określonym oprogramowaniem zarejestrowanym w aplecie Dodaj/Usuń programy lub Programy i funkcje.|  
|**Liczba wszystkich spisanych produktów i ich wersji**|Przedstawia listę programów i wersji uwzględnionych w spisie oraz liczbę komputerów, na których zainstalowano każdy z nich.|  
|**Liczba spisanych produktów i wersji określonego produktu**|Przedstawia listę wersji określonego produktu uwzględnionych w spisie oraz liczbę komputerów, na których zainstalowano każdą z nich.|  
|**Liczba wszystkich wystąpień oprogramowania zarejestrowanego w aplecie Dodaj / Usuń programy**|Przedstawia podsumowanie wszystkich wystąpień oprogramowania zainstalowanego i zarejestrowanego przy użyciu apletu Dodaj/Usuń programy lub Programy i funkcje na komputerach w określonej kolekcji.|  
|**Liczba wystąpień określonego oprogramowania zarejestrowanego w aplecie Dodaj / Usuń programy**|Przedstawia liczbę wystąpień dla określonych pakietów oprogramowania zainstalowanych i zarejestrowanych w aplecie Dodaj/Usuń programy lub Programy i funkcje.|  
|**Domyślna liczba przeglądarki**|Informuje o liczbie klientów przy użyciu przeglądarki sieci web określonego jako domyślny systemu Windows. </br>Użyj następującego odwołania dla typowych BrowserProgIDs:</br> - AppXq0fevzme2pys62n3e0fbqa7peapykr8v: Microsoft Edge</br> -IE. HTTP: Microsoft Internet Explorer</br> -ChromeHTML: Google Chrome</br> -OperaStable: Opera oprogramowania</br> - FirefoxURL-308046B0AF4A39CB: Mozilla Firefox</br> -Nieznane: kliencki system operacyjny nie obsługuje zapytania, zapytanie nie zostało uruchomione lub użytkownik nie zalogowany|
|**Instalacje określonych aplikacji systemu Windows**|Przedstawia listę wszystkich komputerów z określoną aplikacją systemu Windows.|  
|**Produkty na określonym komputerze**|Przedstawia podsumowanie programów uwzględnionych w spisie i ich producentów na określonym komputerze.|  
|**Oprogramowanie zarejestrowane w aplecie Dodaj Usuń programy na określonym komputerze**|Przedstawia podsumowanie wszystkich programów zainstalowanych na określonym komputerze, które zarejestrowano w aplecie Dodaj/Usuń programy lub Programy i funkcje.|  
|**Aplikacje systemu Windows zainstalowane dla określonego użytkownika.**|Przedstawia wszystkie aplikacje systemu Windows zainstalowane dla określonego użytkownika.|  



## <a name="software---files"></a>Oprogramowanie — pliki  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie spisane pliki określonego produktu**|Przedstawia podsumowanie plików uwzględnionych w spisie i skojarzonych z określonym programem.|  
|**Wszystkie spisane pliki na określonym komputerze**|Przedstawia podsumowanie wszystkich plików uwzględnionych w spisie i przechowywanych na określonym komputerze.|  
|**Porównanie spisu oprogramowania na dwóch komputerach**|Przedstawia różnice między spisami oprogramowania zgłoszonymi dla dwóch określonych komputerów.|  
|**Komputery z określonym plikiem**|Przedstawia listę komputerów, na których zgromadzono dane spisu oprogramowania dla określonej nazwy pliku. Jeśli komputer zawiera wiele kopii pliku, może być wyświetlany więcej niż raz na liście.|  
|**Liczba komputerów z określoną nazwą pliku**|Przedstawia liczbę komputerów, na których zgromadzono dane spisu oprogramowania dla określonego pliku.|  



## <a name="software-distribution---application-monitoring"></a>Dystrybucja oprogramowania — monitorowanie aplikacji  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie wdrożenia aplikacji (zaawansowane)**|Przedstawia szczegółowe podsumowanie informacji na temat wszystkich wdrożeń aplikacji.|  
|**Wszystkie wdrożenia aplikacji (basic)**|Przedstawia podsumowanie informacji na temat wszystkich wdrożeń aplikacji.|  
|**Zgodność aplikacji**|Przedstawia informacje na temat zgodności dla określonej aplikacji w określonej kolekcji.|  
|**Wdrożenia aplikacji na zasób**|Przedstawia aplikacje wdrożone do określonego urządzenia lub użytkownika.|  
|**Szczegóły błędów infrastruktury aplikacji**|Przedstawia błędy infrastruktury aplikacji. Błędy te mogą być problemy wewnętrznej infrastruktury, lub błędy wynikające z nieprawidłowych reguł wymagań.|  
|**Szczegółowy stan użytkowania aplikacji**|Przedstawia szczegóły użycia zainstalowanych aplikacji.|  
|**Podsumowanie stanu użycia aplikacji**|Przedstawia podsumowanie użycia zainstalowanych aplikacji.|  
|**aplikacje systemu iOS z nieudanymi wdrożeniami (aplikacja jest już zainstalowana)**|Wyświetla informacje o zgodności wybranej aplikacji systemu iOS. Ta aplikacja została wdrożona jako "pakiet aplikacji dla systemu iOS ze sklepu App Store", który również skojarzone z zasadami zarządzania aplikacjami mobilnymi. Ten raport zawiera informacje o użytkownikach i urządzeniach, dla których instalacja aplikacji nie powiodła się, ponieważ aplikacja została już ręcznie zainstalowana przez użytkownika.|  
|**Wdrożenia sekwencji zadań zawierające aplikację**|Przedstawia wdrożenia sekwencji zadań, które umożliwiają zainstalowanie określonej aplikacji.|  
|**Żądania użytkowników dla aplikacji systemu Android**|Przedstawia użytkowników, którzy zażądali zainstalowania aplikacji systemu Android.|  



## <a name="software-distribution---collections"></a>Dystrybucja oprogramowania — kolekcje  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie kolekcje**|Przedstawia wszystkie kolekcje w hierarchii.|  
|**Wszystkie zasoby w określonej kolekcji**|Przedstawia wszystkie zasoby w określonej kolekcji.|  
|**Okna obsługi dostępne dla określonego klienta**|Przedstawia wszystkie okna obsługi, które można zastosować do określonego klienta.|  



## <a name="software-distribution---content"></a>Dystrybucja oprogramowania — zawartość  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie aktywne dystrybucje zawartości**|Przedstawia wszystkie punkty dystrybucji, w których zawartość jest obecnie instalowana lub usuwana.|  
|**Cała zawartość**|Przedstawia wszystkie aplikacje i pakiety w lokacji.|  
|**Cała zawartość w określonym punkcie dystrybucji**|Przedstawia całą zawartość aktualnie instalowaną w określonym punkcie dystrybucji.|  
|**Wszystkie punkty dystrybucji**|Przedstawia informacje na temat punktów dystrybucji dla każdej lokacji.|  
|**Wszystkie komunikaty o stanie dla określonego pakietu w określonym punkcie dystrybucji**|Przedstawia wszystkie komunikaty o stanie dla określonego pakietu w określonym punkcie dystrybucji.|  
|**Stan dystrybucji zawartości aplikacji**|Przedstawia informacje na temat stanu dystrybucji zawartości aplikacji.|  
|**Aplikacje przeznaczone dla grupy punktów dystrybucji**|Przedstawia informacje na temat zawartości aplikacji, która została wdrożona do określonej grupy punktów dystrybucji.|  
|**Aplikacje niezsynchronizowane w dystrybucji określonej grupie punktów**|Przedstawia aplikacje, dla których skojarzone pliki zawartości nie zostały zaktualizowane do najnowszej wersji w określonej grupie punktów dystrybucji.|  
|**Grupy punktów dystrybucji**|Przedstawia informacje na temat określonej grupy punktów dystrybucji.|  
|**Podsumowanie użycia punktu dystrybucji**|Przedstawia podsumowanie użycia każdego z punktów dystrybucji.|  
|**Stan dystrybucji określonego pakietu**|Przedstawia stan dystrybucji zawartości określonego pakietu w każdym punkcie dystrybucji.|  
|**Pakiety przeznaczone do grupy punktów dystrybucji**|Przedstawia informacje na temat pakietów przeznaczonych dla określonej grupy punktów dystrybucji.|  
|**Pakiety niezsynchronizowane w dystrybucji określonej grupie punktów**|Przedstawia pakiety, dla których skojarzone pliki zawartości nie zostały zaktualizowane do najnowszej wersji w określonej grupie punktów dystrybucji.|  
|**Odrzucenia zawartości równorzędnej pamięci podręcznej źródła**|Wyświetla liczbę równorzędnej pamięci podręcznej źródła odrzuceń dla każdej grupy granic.|
|**Zawartości odrzucenia źródła równorzędnej pamięci podręcznej przez warunek**|Wyświetla źródła pamięci podręcznej elementów równorzędnych, którzy odrzucili do obsługi zawartości na podstawie warunku.|
|**Szczegóły zawartości odrzucenia źródła pamięci podręcznej elementów równorzędnych**|Wyświetla nazwę zawartości, która została odrzucona przez źródło równorzędnej.|



## <a name="software-distribution---package-and-program-deployment"></a>Dystrybucja oprogramowania - wdrażanie pakietów i programów  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie wdrożenia określonego pakietu lub programu**|Przedstawia informacje na temat wszystkich wdrożeń określonego pakietu i programu.|  
|**Wszystkie wdrożenia pakietów i programów**|Przedstawia wszystkie wdrożenia pakietów i programów w danej lokacji.|  
|**Wszystkie wdrożenia pakietów i programów w określonej kolekcji**|Przedstawia wszystkie wdrożenia pakietów i programów do określonej kolekcji.|  
|**Wszystkie wdrożenia pakietów i programów na określonym komputerze**|Przedstawia wszystkie wdrożenia pakietów i programów zastosowane na określonym komputerze.|  
|**Wszystkie wdrożenia pakietów i programów dla określonego użytkownika**|Przedstawia wszystkie wdrożenia pakietów i programów do określonego użytkownika.|  



## <a name="software-distribution---package-and-program-deployment-status"></a>Dystrybucja oprogramowania — stan pakietów i programów wdrożenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie wdrożenia zasobów systemu pakietów i programów o stanie**|Przedstawia wszystkie wdrożenia pakietów i programów dla lokacji oraz podsumowanie stanu każdego wdrożenia.|  
|**Wszystkie zasoby systemu dla określonego wdrożenia pakietu i programu w określonym stanie**|Przedstawia listę zasobów w określonym stanie dla określonego wdrożenia pakietu i programu.|  
|**Wykres - godzinny stan o wykonania wdrożenia pakietu i programu**|Wyświetla procent komputerów, na których pomyślnie zainstalowano pakiet. Listy są uporządkowane dla każdej godziny, ponieważ administrator tworzy wdrożenia pakietu i programu. W tym raporcie można śledzić średni czas wdrażania pakietu i programu.|  
|**Stan wdrażania pakietów i programów dla określonego klienta i wdrożenia**|Przedstawia komunikaty o stanie zgłoszone dla określonego komputera oraz wdrożenia pakietu i programu.|  
|**Stan określonego wdrożenia pakietu i programu**|Przedstawia podsumowanie stanu określonego wdrożenia pakietu i programu.|  



## <a name="software-metering"></a>Pomiar użytkowania oprogramowania  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie reguły zliczania oprogramowania zastosowanie do tej lokacji**|Przedstawia listę wszystkich reguł pomiaru użytkowania oprogramowania w lokacji.|  
|**Komputery, które mierzonym programem, ale program ten nie został uruchomiony od określonej daty**|Wyświetla wszystkie komputery z określoną mierzoną aplikacją, ale żaden użytkownik nie dysponuje program od określonej daty.|  
|**Komputery które uruchomiły określony zliczany program**|Przedstawia listę komputerów, na których uruchamiano programy zgodne z określoną regułą pomiaru użytkowania oprogramowania w określonym miesiącu i roku.|  
|**Współbieżne użycie wszystkich zliczanych programów**|Przedstawia maksymalną liczbę użytkowników, którzy jednocześnie uruchamiali każdy mierzony program w określonym miesiącu i roku.|  
|**Analiza trendu współbieżnego użycia określonego zliczanego programu**|Przedstawia maksymalną liczbę użytkowników, którzy jednocześnie uruchamiali określony mierzony program w każdym miesiącu ostatniego roku.|  
|**Zainstaluj podstawa dla wszystkich zliczanych programów**|Przedstawia liczbę komputerów z zainstalowanymi mierzonymi programami zgłoszonymi w spisie oprogramowania. Ten raport wymaga, aby komputer zbiera dane spisu oprogramowania.|  
|**Postęp podsumowania zliczania oprogramowania**|Przedstawia czas ostatniego przetwarzania zbiorczych danych pomiarów użytkowania na serwerze lokacji. Raporty dotyczące pomiaru użytkowania oprogramowania odzwierciedlać tylko dane zliczania przetworzone przed tymi datami.|  
|**Godzina Podsumowanie użycia określonego zliczanego programu**|Przedstawia średnią liczbę użyć określonego programu w ciągu ostatnich 90 dni z podziałem na godziny i dni.|  
|**Całkowite użycie wszystkich zliczanych programów**|Wyświetla liczbę użytkowników, którzy uruchomili programy w określonym miesiącu i roku i zgodnego z poszczególnymi regułami zliczania oprogramowania. Te reguły dotyczą oprogramowania zainstalowane lokalnie lub przy użyciu usług terminalowych.|  
|**Całkowite użycie wszystkich zliczanych programów na serwerach terminali systemu Windows**|Przedstawia liczbę użytkowników, którzy uruchamiali programy pasujące do każdej reguły pomiaru użytkowania oprogramowania za pomocą usług terminalowych w określonym miesiącu i roku.|  
|**Analiza trendu łącznego użycia określonego zliczanego programu**|Wyświetla liczbę użytkowników, którzy uruchomili programy w poszczególnych miesiącach ubiegłego roku i spełniających określonej reguły pomiaru użytkowania oprogramowania. Te reguły dotyczą oprogramowania zainstalowane lokalnie lub przy użyciu usług terminalowych.|  
|**Analiza trendu łącznego użycia określonego zliczanego programu na serwerach terminali systemu Windows**|Wyświetla liczbę użytkowników, którzy uruchomili programy w poszczególnych miesiącach ubiegłego roku i spełniających określonej reguły pomiaru użytkowania oprogramowania. Te reguły dotyczą przy użyciu usług terminalowych.|  
|**Użytkownicy którzy uruchomili określony zliczany program**|Wyświetla listę użytkowników, którzy uruchomili programy w określonym miesiącu i roku i spełniających określonej reguły pomiaru użytkowania oprogramowania.|  



## <a name="software-updates---a-compliance"></a>Aktualizacje oprogramowania — zgodność  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zgodność 1 - zgodność ogólna**|Przedstawia ogólne dane zgodności dla grupy aktualizacji oprogramowania.|  
|**Zgodność 2 - określona aktualizacja oprogramowania**|Przedstawia dane zgodności określonej aktualizacji oprogramowania.|  
|**Zgodność 3 - grupa aktualizacji (według aktualizacji)**|Przedstawia dane zgodności aktualizacji oprogramowania zdefiniowanych w ramach grupy aktualizacji oprogramowania.|  
|**Zgodność 4 - aktualizacje według dostawcy miesiąca i roku**|Przedstawia dane zgodności aktualizacji oprogramowania wydawanych przez dostawcę w określonym miesiącu i roku.|  
|**Zgodność 5 — określony komputer**|Ten raport zwraca dane zgodności aktualizacji oprogramowania dla określonego komputera. Aby ograniczyć ilość zwracanych informacji, można określić dostawcę i klasyfikację aktualizacji oprogramowania.|  
|**Zgodność 6 - stany określonej aktualizacji oprogramowania (pomocniczy)**|Przedstawia liczbę i procent komputerów w każdym stanie zgodności dla określonej aktualizacji oprogramowania.|  
|**Zgodność 7 - komputery z określonym stanem zgodności dla grupy aktualizacji (pomocniczy)**|Przedstawia wszystkie komputery w kolekcji, które mają określony ogólny stan zgodności względem grupy aktualizacji oprogramowania.|  
|**Zgodność 8 - komputery w określonym stanie zgodności dla aktualizacji (pomocniczy)**|Przedstawia wszystkie komputery w kolekcji, które mają określony ogólny stan zgodności dla aktualizacji oprogramowania.|  



## <a name="software-updates---b-deployment-management"></a>Aktualizacje oprogramowania — Zarządzanie wdrażaniem B  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zarządzanie 1 - wdrożenia grupy aktualizacji**|Przedstawia wszystkie wdrożenia, które zawierają wszystkie aktualizacje oprogramowania zdefiniowane w określonej grupie aktualizacji oprogramowania.|  
|**Zarządzanie 2 - aktualizacje wymagane lecz Niewdrożone**|Wyświetla wszystkie aktualizacje oprogramowania specyficznych dla dostawcy, którzy klienci wykrywają zgodnie z wymaganiami, ale administrator nie zostało wdrożone w określonej kolekcji.|  
|**Zarządzanie 3 - aktualizacje we wdrożeniu**|Przedstawia aktualizacje oprogramowania, które znajdują się w określonym wdrożeniu.|  
|**Zarządzanie 4 - wdrożenia przeznaczone dla kolekcji**|Przedstawia wszystkie wdrożenia aktualizacji oprogramowania, które są przeznaczone dla określonej kolekcji.|  
|**Zarządzanie 5 - wdrożenia przeznaczone dla komputera**|Przedstawia wszystkie wdrożenia aktualizacji oprogramowania, które są przeznaczone dla określonego komputera.|  
|**Zarządzanie 6 - wdrożenia zawierające określoną aktualizację**|Przedstawia wszystkie wdrożenia zawierające określoną aktualizację oprogramowania i skojarzoną kolekcję docelową dla wdrożenia.|  
|**Zarządzanie 7 - aktualizacje wdrożenia z niepełną zawartością**|Przedstawia aktualizacje oprogramowania w określonym wdrożeniu, którego nie pobrano całej skojarzonej zawartości. Ten stan uniemożliwia klientom zainstalowanie aktualizacji, co uniemożliwia osiągnięcie 100% zgodności wdrożenia.|  
|**Zarządzanie 8 - komputery z niepełną zawartością (pomocniczy)**|Wyświetla wszystkie komputery z określonym oprogramowaniem wymagające aktualizacji, ale skojarzonej zawartości, nie jest jeszcze rozprowadzone do punktu dystrybucji.|  



## <a name="software-updates---c-deployment-states"></a>Aktualizacje oprogramowania — stany wdrożeń C  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Stany 1 - stany wymuszenia wdrożenia**|Przedstawia stany wymuszania dla określonego wdrożenia aktualizacji oprogramowania. Zwykle jest to drugi etap oceny wdrożenia.|  
|**Stany 2 - stany oceny wdrożenia**|Przedstawia stany oceniania dla określonego wdrożenia aktualizacji oprogramowania. Zwykle jest to pierwszy etap oceny wdrożenia.|  
|**Stany 3 — stany wdrożenia i komputera**|Przedstawia stany wszystkich aktualizacji oprogramowania określonego wdrożenia dla określonego komputera.|  
|**Stany 4 - komputery z określonym stanem wdrożenia (pomocniczy)**|Przedstawia wszystkie komputery w określonym stanie dla wdrożenia aktualizacji oprogramowania.|  
|**Stany 5 - stany aktualizacji we wdrożeniu (pomocniczy)**|Przedstawia podsumowanie stanów dla aktualizacji oprogramowania związanej z określonym wdrożeniem.|  
|**Stany 6 — komputery z określonym stanem wymuszenia dla aktualizacji (pomocniczy)**|Przedstawia wszystkie komputery w określonym stanie wymuszania dla określonej aktualizacji oprogramowania.|  



## <a name="software-updates---d-scan"></a>Aktualizacje oprogramowania — skanowanie D  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Skanowanie 1 - ostatnie stany skanowania według kolekcji**|Określ kolekcję, aby wyświetlić liczbę komputerów z poszczególnymi stanami skanowania zgodności. Klienci będą zwracać stan podczas ostatniego skanowania zgodności.|  
|**Skanowanie 2 — stany ostatniego skanowania według lokacji**|Określ lokację, aby wyświetlić liczbę komputerów z poszczególnymi stanami skanowania zgodności. Klienci będą zwracać stan podczas ostatniego skanowania zgodności.|  
|**Skanowanie 3 - klienci w kolekcji raportujący określony stan (pomocniczy)**|Przedstawia wszystkie komputery dla określonej kolekcji i określonego stanu skanowania zgodności podczas ich ostatniego skanowania pod kątem zgodności.|  
|**Skanowanie 4 — klienci w lokacji raportujący określony stan (pomocniczy)**|Określ lokację, aby wyświetlić wszystkie komputery z określonego stanu skanowania zgodności. Klienci będą zwracać stan podczas ich ostatniego skanowania zgodności.|  



## <a name="software-updates---e-troubleshooting"></a>Aktualizacje oprogramowania — Rozwiązywanie problemów E  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Rozwiązywanie problemów 1 — błędy skanowania**|Przedstawia błędy skanowania w lokacji oraz liczbę komputerów, na których występuje każdy z błędów.|  
|**Rozwiązywanie problemów 2 – błędy wdrożenia**|Przedstawia błędy wdrożenia w lokacji oraz liczbę komputerów, na których występuje każdy z błędów.|  
|**Rozwiązywanie problemów 3 - komputery z niepowodzeniem skanowania z powodu określonego błędu (pomocniczy)**|Przedstawia listę komputerów, których skanowanie nie powiodło się z powodu określonego błędu.|  
|**Rozwiązywanie problemów 4 - komputery z niepowodzeniem z powodu określonego błędu wdrożenia (pomocniczy)**|Przedstawia listę komputerów, na których wdrażanie aktualizacji nie powiodło się z powodu określonego błędu.|  



## <a name="state-migration"></a>Migracja stanu  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Informacje o migracji stanu dla określonego komputera źródłowego**|Przedstawia informacje na temat migracji stanu dla określonego komputera.|  
|**Informacje o migracji stanu dla określonego punktu migracji stanu**|Przedstawia informacje na temat migracji stanu dla określonego punktu migracji stanu.|  
|**Punkty migracji stanu dla określonej lokacji**|Przedstawia punkty migracji stanu dla określonej lokacji.|  



## <a name="status-messages"></a>Komunikaty o stanie  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie komunikaty z określonym Identyfikatorem komunikatu**|Przedstawia listę komunikatów o stanie z określonym identyfikatorem komunikatu.|  
|**Klienci raportujący błędy w ciągu ostatnich 12 godzin dla określonej lokacji**|Przedstawia listę komputerów i składników zgłaszających błędy w ciągu ostatnich 12 godzin oraz liczbę zgłoszonych błędów.|  
|**Komunikaty składników z ostatnich 12 godzin**|Przedstawia listę komunikatów składników z ostatnich 12 godzin dla określonego kodu lokacji, komputera i składnika.|  
|**Komunikaty składników z ostatniej godziny**|Wyświetla listę komunikatów o stanie utworzonych w ciągu ostatniej godziny przez określony składnik na określonym komputerze w określonej lokacji.|  
|**Liczba komunikatów składników z ostatniej godziny dla określonej lokacji**|Przedstawia liczbę komunikatów o stanie zgłoszonych w ciągu ostatniej godziny w określonej lokacji i uporządkowanych według składnika i ważności.|  
|**Liczba błędów w ciągu ostatnich 12 godzin**|Przedstawia liczbę komunikatów o stanie błędów składników serwera w ciągu ostatnich 12 godzin.|  
|**Błędy krytyczne (według składnika)**|Przedstawia listę komputerów zgłaszających błędy krytyczne uporządkowaną według składnika.|  
|**Błędy krytyczne (według nazwy komputera)**|Przedstawia listę komputerów zgłaszających błędy krytyczne uporządkowaną według nazwy komputera.|  
|**Ostatnie 1000 komunikatów dla określonego komputera (błędy i ostrzeżenia)**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie składnika wskazujących na błąd i ostrzeżenie dla określonego komputera.|  
|**Ostatnie 1000 komunikatów dla określonego komputera (błędy ostrzeżenia i informacje)**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie składnika wskazujących na błąd, ostrzeżenie i informacje dla określonego komputera.|  
|**Ostatnie 1000 komunikatów dla określonego komputera (błędy)**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie składnika wskazujących na błąd dla określonego komputera.|  
|**Ostatnie 1000 komunikatów dla określonego składnika serwera**|Przedstawia podsumowanie ostatniego 1000 komunikatów o stanie dla określonego składnika serwera.|  



## <a name="status-messages---audit"></a>Komunikaty o stanie — inspekcja  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie komunikaty audytu dla określonego użytkownika**|Przedstawia podsumowanie wszystkich komunikatów inspekcji dla określonego użytkownika. Komunikaty inspekcji opisują akcje wykonywane w konsoli programu Configuration Manager, które dodawania, modyfikowania i usuwania obiektów w programie Configuration Manager.|  
|**Sterowanie zdalne - wszystkie komputery zdalnie sterowane przez określonego użytkownika**|Przedstawia podsumowanie komunikatów o stanie wskazujących na zdalne sterowanie komputerami klienckimi przez określonego użytkownika.|  
|**Sterowanie zdalne - wszystkie informacje dotyczące sterowania zdalnego**|Przedstawia podsumowanie komunikatów o stanie powiązanych ze zdalnym sterowaniem komputerami klienckimi.|  



## <a name="task-sequence---deployment-status"></a>Sekwencja zadań — stan wdrożenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie zasoby systemowe dla wdrożenia sekwencji zadań w określonym stanie**|Przedstawia listę komputerów docelowych dla określonego wdrożenia sekwencji zadań w określonym stanie wdrożenia.|  
|**Wszystkie zasoby systemowe dla wdrożenia sekwencji zadań, który znajduje się w określonym stanie i że jest dostępne dla nieznanych komputerów**|Przedstawia listę komputerów docelowych dla określonego wdrożenia sekwencji zadań w określonym stanie wdrożenia.|  
|**Liczba zasobów systemowych, które mają wdrożenia sekwencji zadań przypisane, ale nie został jeszcze uruchomiony**|Przedstawia liczbę komputerów z zaakceptowanymi sekwencjami zadań, dla których nie uruchomiono sekwencji zadań.|  
|**Historia wdrożenia sekwencji zadań na komputerze**|Przedstawia stan każdego kroku wdrożenia sekwencji zadań na określonym komputerze docelowym. Jeśli żadne rekordy nie zostaną zwrócone, sekwencja zadań nie została uruchomiona na komputerze.|  
|**Lista komputerów które został przekroczony czas uruchamiania wdrożenia sekwencji zadań**|Przedstawia listę komputerów, dla których czas uruchamiania sekwencji zadań jest dłuższy niż określona wartość.|  
|**Czas wykonywania dla określonego wdrożenia sekwencji zadań na określonym komputerze docelowym**|Przedstawia całkowity czas pomyślnego wykonywania określonej sekwencji zadań na określonym komputerze.|  
|**Uruchom czasu dla każdego kroku wdrożenia sekwencji zadań na określonym komputerze docelowym**|Przedstawia czas wykonywania każdego kroku określonego wdrożenia sekwencji zadań na określonym komputerze docelowym.|  
|**Stan określonego wdrożenia sekwencji zadań dla określonego komputera**|Przedstawia podsumowanie stanu określonego wdrożenia sekwencji zadań na określonym komputerze.|  
|**Stan wdrożenia sekwencji zadań na nieznanym komputerze docelowym**|Przedstawia stan określonego wdrożenia sekwencji zadań na określonym nieznanym komputerze docelowym.|  
|**Podsumowanie stanu określonego wdrożenia sekwencji zadań**|Przedstawia podsumowanie stanu wszystkich zasobów przeznaczonych do użycia we wdrożeniu.|  
|**Podsumowanie stanu określonego wdrożenia sekwencji zadań dostępne dla nieznanych komputerów**|Wyświetla podsumowanie stanu wszystkich zasobów objęci określonego wdrożenia, który jest dostępny do kolekcji zawierającej nieznane komputery.|  



## <a name="task-sequence---deployments"></a>Sekwencja zadań — wdrożenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie zasoby systemowe obecnie w określonej grupie lub fazie określonego wdrożenia sekwencji zadań**|Przedstawia listę komputerów, które obecnie działają w ramach określonej grupy lub fazy określonego wdrożenia sekwencji zadań.|  
|**Wszystkie zasoby systemowe, których wdrożenie sekwencji zadań w określonej grupie lub fazie zakończyło się niepowodzeniem**|Przedstawia listę komputerów, na których wystąpiły błędy w ramach określonej grupy lub fazy określonego wdrożenia sekwencji zadań.|  
|**Wszystkie wdrożenia sekwencji zadań**|Przedstawia szczegóły wszystkich wdrożeń sekwencji zadań inicjowanych w bieżącej lokacji.|  
|**Wszystkie wdrożenia sekwencji zadań dostępne dla nieznanych komputerów**|Wyświetla szczegóły wszystkich wdrożeń sekwencji zadań inicjowanych z lokacji i wdrożonych do kolekcji zawierających nieznane komputery.|  
|**Liczba niepowodzeń w każdej fazie lub grupie określonej sekwencji zadań**|Przedstawia liczbę błędów w każdej fazie lub grupie określonej sekwencji zadań.|  
|**Liczba niepowodzeń w każdej fazie lub grupie określonego wdrożenia sekwencji zadań**|Przedstawia liczbę błędów w każdej fazie lub grupie określonego wdrożenia sekwencji zadań.|  
|**Stan wdrożenia wszystkich wdrożeń sekwencji zadań**|Przedstawia ogólny postęp wszystkich wdrożeń sekwencji zadań.|  
|**Postęp wykonywanej sekwencji zadań**|Przedstawia postęp określonej sekwencji zadań.|  
|**Postęp wykonywanego wdrożenia sekwencji zadań**|Przedstawia podsumowanie informacji na temat określonego wdrożenia sekwencji zadań.|  
|**Postęp wszystkich wdrożeń dla określonej sekwencji zadań**|Przedstawia postęp wszystkich wdrożeń określonej sekwencji zadań.|  
|**Raport podsumowania wdrożenia sekwencji zadań**|Przedstawia podsumowanie informacji na temat określonego wdrożenia sekwencji zadań.|  



## <a name="task-sequence---progress"></a>Sekwencja zadań — postęp  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wykres - tygodniowy postęp sekwencji zadań**|Przedstawia tygodniowy postęp sekwencji zadań od daty wdrożenia.|  
|**Postęp sekwencji zadań**|Przedstawia postęp określonej sekwencji zadań.|  
|**Postęp wszystkich sekwencji zadań**|Przedstawia podsumowanie postępu wszystkich sekwencji zadań.|  
|**Postęp sekwencji zadań wdrożeń systemu operacyjnego**|Przedstawia postęp wszystkich sekwencji zadań powodujących wdrażanie systemów operacyjnych.|  
|**Stan wszystkich nieznanych komputerów**|Wyświetla listę komputerów, które były nieznane w momencie wykonywania wdrożenia sekwencji zadań, oraz określa, czy komputery są teraz znane.|  



## <a name="task-sequences---references"></a>Sekwencje zadań — odwołania  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Zawartość z odwołaniami określonej sekwencji zadań**|Przedstawia zawartość, do której odwołuje się sekwencja zadań.|  



<!--
## Upgrade Assessment  

|Report name|Description|  
|-----------------|-----------------|  
|**Application status for a specific computer**|Displays the compatibility of applications that are installed on a computer for a specified operating system.|  
|**Application status for computers in a specific collection**|Displays the overall status for computers in a collection to let you assess them for upgrade to a specified operating system based on the applications on each computer. Use this report to determine which computers have compatible applications before you deploy an operating system.|  
|**Application status summary**|Displays a summary of the application status for a specified operating system. Use this report to determine application compatibility before you deploy an operating system.|  
|**Computers with a specific application installed**|Displays computers with a specified application installed.|  
|**Computers with a specific hardware device**|Displays computers that have a specific hardware device.|  
|**Hardware device status for a specific computer**|Displays the compatibility status of hardware devices for a specified operating system that are found on a specified computer.|  
|**Hardware device status for computers in a specific collection**|Displays the overall status for hardware devices for a specified operating system for computers in a specified collection. Use this report to determine hardware compatibility before you deploy an operating system.|  
|**Hardware device status summary**|Displays a summary of hardware device status for a specified operating system. You can use this report to determine hardware device compatibility before you deploy an operating system.|  
|**Operating system hardware requirements**|Displays the minimum and recommended hardware criteria for operating systems.|  
|**Operating system requirement status for computers in a specific collection**|Displays the status of operating system requirements for the specified operating system for computers in a specified collection. Use this report to determine if a computer meets the specified operating system requirements for CPU processor speed, memory size, and hard disk space.|  
|**Upgrade assessment summary**|Displays the upgrade assessment summary. You can use this report to assess the overall status for upgrade compatibility.|  
-->



## <a name="user---device-affinity"></a>Użytkownik — koligacja urządzenia  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Powiązania koligacji urządzeń użytkownika oczekujące według kolekcji**|Przedstawia wszystkie oczekujące przypisania koligacji urządzenia użytkownika w oparciu o dane użycia dla elementów członkowskich kolekcji.|  
|**Powiązania koligacji urządzeń użytkownika na kolekcję**|Wyświetla wszystkie skojarzenia urządzeń użytkowników dla określonej kolekcji oraz grupuje wyniki według typu kolekcji (na przykład użytkownika lub urządzenia).|  



## <a name="user-data-and-profiles-health"></a>Kondycja profili i danych użytkownika  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Raport kondycji przekierowania folderów — szczegóły**|Wyświetla szczegóły stanu kondycji przekierowania folderu dla każdego z przekierowanych folderów dla danego użytkownika.|  
|**Mobilnego raport o kondycji profilu użytkownika — szczegóły**|Wyświetla szczegóły stanu kondycji profilu użytkownika mobilnego dla określonego użytkownika.|  
|**Raport dane użytkownika i kondycja profilów - szczegóły**|Wyświetla błąd lub ostrzeżenie szczegóły Przekierowanie folderu lub profilów użytkowników mobilnych. Ten raport jest elementem docelowym szczegóły z raportu podsumowującego.|  
|**Dane użytkownika raport i kondycja profilów - podsumowanie**|Przedstawia podsumowanie stanów kondycji przekierowania folderu i profili użytkowników mobilnych.|  



## <a name="users"></a>Użytkownicy  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Komputery z określoną nazwą użytkownika**|Przedstawia listę komputerów, które były używane przez określonego użytkownika.|  
|**Liczba użytkowników według domeny**|Przedstawia liczbę użytkowników w każdej domenie.|  
|**Użytkownicy w określonej domenie**|Przedstawia listę użytkowników i ich komputerów w określonej domenie.|  



## <a name="virtual-applications"></a>Aplikacje wirtualne  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wyniki środowiska wirtualnego App-V**|Przedstawia informacje o określonym środowisku wirtualnym, które znajduje się w określonym stanie względem wybranej kolekcji.|  
|**Wyniki środowiska wirtualnego App-V dla zasobu**|Wyświetla informacje o określonym środowisku wirtualnym przy określonym zasobie. Przedstawia on także żadnych typów wdrożenia dla określonego środowiska wirtualnego.|  
|**Status środowiska wirtualnego App-V**|Przedstawia informacje na temat zgodności określonego środowiska wirtualnego z określoną kolekcją.|  
|**Komputery z określoną aplikacją wirtualną**|Przedstawia podsumowanie komputerów z określonym skrótem aplikacji App-V utworzonym przy użyciu aplikacji Application Virtualization Management Sequencer.|  
|**Komputery z określonym pakietem aplikacji wirtualnych**|Wyświetla podsumowanie komputerów z określonym pakietem aplikacji App-V.|  
|**Liczba wszystkich wystąpień pakietów aplikacji wirtualnych**|Przedstawia liczbę wykrytych pakietów aplikacji App-V.|  
|**Liczba wszystkich wystąpień aplikacji wirtualnych**|Przedstawia liczbę wykrytych aplikacji App-V.|  



## <a name="volume-purchase-programs---apple"></a>Programów Volume Purchase - firmy Apple

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Aplikacje programu Apple Volume Purchase Program dla systemu iOS z liczbami licencji**|Wyświetla wszystkie urządzenia iPhone, tabletów iPad i iPod aplikacji Touch licencjonowanych w ramach programu zakupów zbiorczych firmy Apple. Ten raport zawiera również razem zakupionych licencji i licencji zużytych według aplikacji.|  



## <a name="vulnerability-assessment"></a>Oceny luk w zabezpieczeniach

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Ogólny raport oceny luk**|Identyfikuje zabezpieczeń administracyjnych i luk w zabezpieczeniach zgodności dla określonego komputera|  



## <a name="wake-on-lan"></a>Wake On LAN  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|**Wszystkie komputery ustawione na aktywność funkcji Wake On LAN**|Określ typ wdrożenia, aby wyświetlić listę komputerów, przeznaczone do wznawiania działania sieci LAN.|  
|**Wszystkie obiekty oczekujące na wznowienie**|Przedstawia obiekty zaplanowane do wznowienia.|  
|**Wszystkie lokacje z włączoną funkcją Wake On LAN**|Przedstawia listę wszystkich lokacji w hierarchii, które zostały włączone dla działania Wake On LAN.|  
|**Błędy otrzymane podczas wysyłania pakietów wznowienia w określonym przedziale czasu**|Przedstawia błędy odebrane podczas wysyłania pakietów do komputerów w zdefiniowanym okresie.|  
|**Historia aktywności funkcji Wake On LAN**|Przedstawia historię działania wznawiania w danym okresie.|  
|**Szczegóły stanu wdrażania serwera Proxy wznawiania**|Przedstawia informacje na temat stanu wdrożenia serwera proxy wznawiania dla każdego urządzenia w określonej kolekcji.|  
|**Podsumowanie stanu wdrażania serwera Proxy wznawiania**|Przedstawia podsumowanie stanu wdrożenia serwera proxy wznawiania w określonej kolekcji.|  
