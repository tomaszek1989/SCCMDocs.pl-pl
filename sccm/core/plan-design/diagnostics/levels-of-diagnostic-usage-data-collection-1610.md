---
title: Dane diagnostyczne dla 1610 | System Center Configuration Manager
description: "Więcej informacji na temat poziomów diagnostyki i System Center Configuration Manager w wersji 1610 służy do zbierania danych użycia."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: eb20eb90-bcc0-41de-bfea-638ea470c0dd
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ba1e53fdc895690bb958c12d59f82a26067ecad3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="levels-of-diagnostic-usage-data-collection-for-version-1610-of-system-center-configuration-manager"></a>Poziomy zbierania danych diagnostycznych użycia wersja 1610 dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager w wersji 1610 zbiera trzy poziomy diagnostyki i dane dotyczące użycia: **Podstawowe**, **rozszerzone**, i **pełne**. Domyślnie ta funkcja jest ustawiona na poziomie rozszerzonym. Poniższe sekcje zawierają dodatkowe szczegóły dotyczące danych, która gromadzi każdy poziom.

Odnotowano zmian w porównaniu z poprzednimi wersjami z ***[New]***, ***[zaktualizowane]***, ***[usunięte]***, lub ***[przenieść]***.


> [!IMPORTANT]
>  Menedżer konfiguracji nie zbiera kody lokacji, witryn nazwisk, adresów IP, nazwy użytkowników, nazwy komputerów, adresów fizycznych ani adresów e-mail na poziomach Basic lub rozszerzonego. Wszelkie zbierania tych informacji na poziomie pełnego nie jest purposeful, oznacza to, potencjalnie uwzględnione w zaawansowane informacje diagnostyczne, takie jak pliki dziennika lub migawki pamięci. Firma Microsoft nie użyje tych informacji do identyfikacji użytkownika, kontaktu lub rozwoju reklamy.

##  <a name="bkmk_change"></a> Jak zmienić poziom
 Administratorzy, którzy mają zakres administracyjny opartej na rolach zawierający **Modyfikuj** uprawnienia na **witryny** klasy obiektów można zmienić poziom danych zebranych w ustawieniach diagnostyki i użycia danych w konsoli programu Configuration Manager.

Począwszy od wersji 1610, zmień poziom kolekcji danych z konsoli programu przechodząc do **Administracja** > **Przegląd** > **konfiguracja lokacji** > **witryny**. Otwórz **ustawienia hierarchii**, a następnie wybierz poziom danych, którego chcesz użyć.  

##  <a name="bkmk_level1"></a> Poziom 1 — podstawowy
 Poziom podstawowy zawiera dane o hierarchii, dane, które są wymagane, aby pomóc poprawić instalacji lub uaktualnienia doświadczenie i danych, która pozwala na zidentyfikowanie aktualizacji programu Configuration Manager, które są stosowane dla hierarchii.

 Programu System Center Configuration Manager wersji 1610 ten poziom jest następująca:


-   Informacje o konfiguracji:
       - Tworzenie, zainstaluj typu, pakiety językowe, funkcje, które włączono  

       - Zaktualizuj stan wdrożenia pakietów i błędy, Pobierz postępu i błędy wymagań wstępnych     

       - Wersja skryptu po uaktualnieniu

       - Użyj pierścienia szybkie aktualizacji

    - ***[New] *** w wersji wstępnej stosowania, typ nośnika instalacji, typ gałęzi

    - ***[New] *** Software Assurance Data wygaśnięcia

- Metryki wydajności bazy danych (informacje na temat przetwarzania replikacji, najważniejsze procedury składowane programu SQL według użycia dysku i procesora)

- Konfiguracja podstawowej bazy danych (procesory, konfiguracji klastra i konfiguracji widoków rozproszonych)

- Schemat bazy danych programu Configuration Manager (skrót wszystkich definicji obiektu)

- Wersje klienta liczba programu Configuration Manager i systemu operacyjnego

- Liczba systemów operacyjnych dla zarządzanych urządzeń i zasad ustawionych przez program Exchange Connector

- Liczba języków klienta i ustawień regionalnych

- Liczba urządzeń z systemem Windows 10 według gałęzi i kompilacji

- Podstawowe programu Configuration Manager hierarchii danych lokacji (witryny, listy, typu, wersji, stan, liczba klientów i strefy czasowej)

- Podstawowy serwer informacje o systemie lokacji (Role systemu lokacji używana, stan Internet i protokołu SSL, system operacyjny, procesory i maszyny fizycznej lub wirtualnej)

- Statystyki odnajdywania użytkownika podstawowego (użytkownika odnajdywania średnią minimum/maksimum i liczba rozmiary grupy)

- Podstawowe informacje Endpoint Protection (wersje ochrony przed złośliwym oprogramowaniem klienta)

- Podstawowy typ wdrożenia aplikacji i zlicza (całkowita liczba aplikacji, całkowita aplikacji przy użyciu wielu typów wdrożeń, całkowita aplikacje z zależnościami, całkowita zastąpione aplikacji oraz liczba technologie wdrażania w użyciu)

- Wdrożenie podstawowego systemu operacyjnego (OSD) zlicza (obrazów)

- Punkt dystrybucji i zarządzania punktu typów oraz informacje o podstawowej konfiguracji (chronione, wstępnie przygotowane, środowisko PXE, multiemisja stanu protokołu SSL, punktów dystrybucji ściągania/peer włączone MDM, włączony protokół SSL, itd.)

- Dane statystyczne telemetrii (czas uruchamiania, środowisko uruchomieniowe, błędy)

- Poziom telemetrii skonfigurowanego, trybie (online lub offline) i szybkie aktualizacji konfiguracji

- Korzystanie z odnajdywania sieci (włączony lub wyłączony)
- Konsola administratora:

     - Statystyki połączeń z konsolą (wersja systemu operacyjnego, języka, SKU i architektura, pamięci, liczbę procesorów logicznych, połączyć identyfikator witryny, zainstalowanych wersji .NET i pakietów językowych konsoli)    

- Wersja programu SQL, poziom dodatku service pack, edition, identyfikator sortowania i zestaw znaków


##  <a name="bkmk_level2"></a> Poziom 2 — rozszerzony
Poziom rozszerzonego jest domyślnie po zakończeniu pracy Instalatora. Ten poziom zawiera dane, które są zbierane w programie poziom podstawowy i danych właściwych dla funkcji (częstotliwość oraz czas trwania użycia), ustawienia klienta programu Configuration Manager (nazwa składnika, stan i niektóre ustawienia, takie jak interwały) i podstawowe informacje o aktualizacji oprogramowania.

Ten poziom jest zalecane, ponieważ firma Microsoft zapewnia minimalne dane, które są wymagane w celu ulepszenia przydatne w przyszłych wersjach produktów i usług. Ten poziom nazwy obiektów nie zbieraj (witryny, użytkowników, komputerów lub obiektów), szczegóły obiektów związanych z zabezpieczeniami lub luk w zabezpieczeniach, takich jak liczby systemów, które wymagają aktualizacji oprogramowania.

Programu System Center Configuration Manager wersji 1610 ten poziom jest następująca:

-   **Zarządzanie aplikacjami:**  

    -    Podstawowe użycie/docelowych informacje dotyczące typów wdrożeń, które są używane w organizacji (użytkowników i urządzeń docelowych, wymagane i aplikacje dostępne i uniwersalnych)  

    -   Informacje na temat wdrażania aplikacji (instalowania/odinstalowywania, wymaga zatwierdzenia, interakcji z użytkownikiem włączone/wyłączone, zależności i zastępowanie)  

    -   Dostępne dane statystyczne żądań dotyczących aplikacji  

    -   Liczba pakietów według typu  

    -   Liczba zastosowań aplikacji według systemu operacyjnego  

    -   Liczba wdrożeń pakietów/programów  

    -   Liczba właściwości wdrożeń i środowisk App-V  

    -   Liczba licencji aplikacji licencjonowanych w systemie Windows 10  

    -   Minimum/maksimum/średnia liczba wdrożeń aplikacji dla użytkowników i urządzeń w okresie

    -   Typ i czas trwania okna obsługi  

    -  Statystyk rozmiar i złożoność zasad aplikacji

    - ***[Zaktualizowane] *** Liczba Sklepu Windows dla aplikacji biznesowych i statystyki synchronizacji (podsumowanie typów aplikacji, w tym licencjonowane stanu aplikacji, a liczba online i offline licencjonowane aplikacje)  

    - Statystyki grupy granic (ile szybkie, jak wiele wolniej, a liczba dla każdej grupy)

    - Opcje konfiguracji MSI i liczby

    - Wymagania dotyczące aplikacji (liczba wbudowanych warunki odwołuje się do niego wdrażania technologii)

    - Zastępowania aplikacji, maksymalna głębokość łańcucha

    - Użycie uniwersalnego dostępu do danych (UDA), jak utworzone

    - ***[New] *** Częstotliwość statystyki i użycia zatwierdzenie aplikacji



-   **Klient:**  

    -   Lista/liczba włączonych agentów klientów  

    -   Liczba instalacji klientów z każdego typu lokalizacji źródłowej  

    -   Liczba błędów instalacji klienta  

    -  ***[Zaktualizowane] *** Automatycznej aktualizacji klienta: konfiguracji wdrażania, w tym piloting i wykluczania wykorzystania (rozszerzonej współdziałanie klienta)

    -  Statystyki kondycji klienta i podsumowanie problemów górny

    - Wiek BIOS w lat.

    - System operacyjny wiek w miesiącach

    - Liczba oprogramowania Centrum akcji

    - Wersja klienta usługi Active technologii zarządzania (AMT)

    - Błędy pobierania wdrożenia klienta

    - Klient powiadomień operacji stanu akcji (ile razy jest wykonywania, maksymalna liczba klientów docelowych i Częstotliwość powodzeń średnia)

    - Metody wdrażania klienta i liczba klientów na metody wdrażania

    - Konfiguracja rozmiar pamięci podręcznej klienta

    - ***[New] *** Liczba klasy spisu sprzętu, oprogramowania spisu reguły i zasady zbierania plików




- **Usługi w chmurze:**

  - Liczba kolekcji zsynchronizowane z programem Operations pakietu zarządzania

  -  Czy został włączony łącznik programu Operations Management Suite chmury

  - ***[New] *** Konfiguracji i użytkowania statystyki brama zarządzania chmury

  - ***[New] *** Liczby łączników Analytics uaktualnienia




- **Kolekcje:**

    -  Zbieranie statystyk oceny (czas kwerendy przypisane w zależności od liczby nieprzypisane, liczba wg typu, identyfikator przerzucania i użycia reguły)

    - Kolekcje bez wdrożenia

    - Użycie identyfikator kolekcji (nie uruchamianie poza identyfikatory)



-   **Ustawienia zgodności:**  

    -   Liczba elementów konfiguracji według typu  

    -   Podstawowe informacje o linii bazowej konfiguracji (liczba, liczba wdrożeń i liczba odwołań)  

    -   Liczba wdrożeń tego ustawienia wbudowanych odwołań (teraz Przechwytywanie skorygować ustawienie)  

    -   Liczba reguł i wdrożeń utworzonych dla ustawień niestandardowych (teraz Przechwytywanie skorygować ustawienie)  
    -   Liczba wdrożonych szablony prostego protokołu rejestrowania certyfikatów (SCEP), sieci VPN, sieci Wi-Fi, certyfikatu (pfx) i zasad zgodności

    -  Liczba SCEP certyfikatu sieci VPN, sieci Wi-Fi, (.pfx) oraz wdrożenia zasad zgodności przez platformę

    - Usługa Passport for zasad pracy (utworzone, wdrożony)



-   **Zawartość:**  

    -   Liczba granic według typu  

    -   Informacje o grupach granic (liczba granice i systemów lokacji, które są przypisane do każdej grupy granic)  

    - ***[New] *** Rezerwowej konfiguracji i relacje grupy granic

    -   Informacje o grupie punktów dystrybucji (liczba pakiety i punkty dystrybucji, które są przypisane do każdej grupy punktów dystrybucji)  

    -   Informacje o konfiguracji punktu dystrybucji (Korzystanie z pamięci podręcznej w oddziale firmy i monitorowania punktu dystrybucji)  

    -   Informacje o konfiguracji Menedżera dystrybucji (wątków, opóźnienie, liczbę ponownych prób i ściągnąć ustawienia punktu dystrybucji)  

    - ***[New] *** Liczba elementów równorzędnych pamięci podręcznej klientów i statystyki użycia

    - ***[New] *** Statystyk pobierania zawartości klienta


-   **Program Program Endpoint Protection:**  

    -   Punkt końcowy ochrony przed złośliwym oprogramowaniem i użycia zasad zapory systemu Windows (liczba unikatowych zasady przypisane grupie)<br /><br /> Nie ma żadnych informacji o ustawieniach zawartych w zasadach.  

    -   Błędy wdrożenia programu Endpoint Protection (liczba kody błędów wdrażania zasad programu Endpoint Protection)  

    -   Liczba kolekcji, które są wybrane pojawią się w pulpit nawigacyjny ochrony punktu końcowego  

    -   Liczba alertów, które są skonfigurowane dla funkcji programu Endpoint Protection  

    -     Zaawansowane zasady ochrony zagrożenia (ATP) (liczba zasad i czy zasady są wdrażane)


- **Migracji:**

  -   Liczba obiektów migrowanych (Użyj Kreatora migracji)



-   **Zarządzanie urządzeniami przenośnymi:**  

    -   ***[Zaktualizowane] *** Liczba wydanych akcji urządzenia przenośnego: blokowanie, przypiąć rest, czyszczenia, wycofanie i zsynchronizować teraz poleceń  

    -   Liczba urządzeń przenośnych, które są zarządzane przez program Configuration Manager i Microsoft Intune i jak zostały zarejestrowane (zbiorczo, oparte na użytkownika)  

    -   Sondowania harmonogram i statystyki dla urządzeń przenośnych ewidencjonowania czas trwania urządzeń przenośnych  

    -   Liczba zasad urządzeń przenośnych  

    -   Liczba użytkowników, którzy mają wiele zarejestrowanych urządzeń przenośnych  

-   **Rozwiązywanie problemów z Microsoft Intune:**

    -   Liczba i rozmiar stan, stan, Magazyn, RDR, DDR, UDX, dzierżawy komunikatów o stanie, znaki, dziennika, certyfikatów, CRP, ponownej synchronizacji, CFD, RDO, BEX, ISM i zgodności pobieranych z Microsoft Intune

    -   Liczba i rozmiar akcji urządzenia (czyszczenie, wycofanie, blokowanie), telemetrii i komunikatów danych, które są replikowane w usłudze Microsoft Intune

    -   Pełne i różnicowe statystyki synchronizacji użytkowników usługi Microsoft Intune


-   **Lokalne zarządzanie urządzeniami przenośnymi:**  

    -   Dane statystyczne powodzeń/niepowodzeń wdrożenia dla lokalnych wdrożeń aplikacji do zarządzania aplikacjami przenośnymi  

    -   Liczba pakietów i profilów rejestrowania zbiorczego w systemie Windows 10  



-   **Wdrożenie systemu operacyjnego:**  

    -   Liczba obrazów rozruchowych, sterowników, pakietów sterowników, punktów dystrybucji z obsługą multiemisji, punktów dystrybucji obsługujących środowisko PXE i sekwencji zadań  

    -   Licznik użycia kroku sekwencji zadań

    - ***[New] *** Liczba zasady uaktualniania wersji



-   **Aktualizacje lokacji:**

    - Wersje zainstalowanych poprawek programu Configuration Manager




-   **Aktualizacje oprogramowania:**  

    -   Wdrożone razem/średnia liczba kolekcji, które wdrożenia aktualizacji oprogramowania i maksymalna/średnia liczba aktualizacji  

    -   Liczba reguł wdrażania automatycznego, które są powiązane z synchronizacji  

    -   Liczba reguł wdrażania automatycznego, które umożliwiają tworzenie nowej grupy aktualizacji lub dodawanie aktualizacji do istniejącej grupy  

    -   Dostępny i terminu zmianami używanych w zasadach wdrażania automatycznego  

    -   Średnia i maksymalna liczba przydziałów na aktualizację  

    -   Liczba aktualizacji są tworzone i wdrażane za pomocą programu System Center Update Publisher  

    -   Liczba przydziałów i grup aktualizacji  

    -   Liczba pakietów aktualizacji i maksimum/minimum/średnią liczbę punktów dystrybucji, ukierunkowane na z pakietami  

    -   Liczba grup aktualizacji oraz maksymalna/minimalna/średnia liczba aktualizacji na grupę  

    -   Liczba aktualizacji i procent aktualizacji, które są wdrożone za wygasłe, zastąpione, pobrane i zawierać umowy licencyjne  

    -   Liczba maszyn i kody błędów skanowania aktualizacji  

    -   Harmonogramy skanowania i oceny aktualizacji klienta  

    -   Harmonogram synchronizacji punktów aktualizacji oprogramowania  

    -   Liczba reguł wdrażania automatycznego, które mają wiele wdrożeń  

    -   Konfiguracje, które są używane do obsługi planów active systemu Windows 10  

    -   Wersje zawartości pulpitu nawigacyjnego systemu Windows 10  

    -   Liczba systemu Windows 10 klientów, którzy używają usługi Windows Update dla firm  

    -   Dane statystyczne poprawek klastrów  

    -   Liczba wdrożonych aktualizacji usługi Office 365  

    -   Klasyfikacje, które są synchronizowane przez punkt aktualizacji oprogramowania

    -   Statystyki równoważenia obciążenia punktu aktualizacji oprogramowania

    -  ***[New] *** Konfiguracji systemu Windows 10 express aktualizacji




-   **Dane wydajności/SQL:**  

    -   Liczba największych tabel bazy danych  

    -   ***[Zaktualizowane] *** Stan repliki funkcji SQL AlwaysOn informacje, użycia i kondycji

    -  Okresu przechowywania śledzenia zmian programu SQL

    - Włączone typy odnajdywania i harmonogram (pełnych, przyrostowych)

    - Odnajdywanie operacyjnej statystyki (liczba znalezionych)

    - Śledzenie problemów z wydajnością, okres przechowywania i stan automatycznego czyszczenia zmian SQL



- **Różne**

    - Liczba miejsc z wznawiania w sieci Lan (WOL)

    - ***[New] *** Raportowania statystyk użycia i wydajności  



##  <a name="bkmk_level3"></a> Poziom 3 — pełny
Pełna poziom zawiera wszystkie dane w poziomy podstawowe i rozszerzone. Zawiera on również dodatkowe informacje na temat programu Endpoint Protection, wartości procentowe zgodności aktualizacji i informacje na temat aktualizacji oprogramowania.  Ten poziom można także zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci, które mogą zawierać informacje osobiste, które istniały w pamięci lub pliki dziennika w czasie przechwytywania.

Programu System Center Configuration Manager wersji 1610 ten poziom jest następująca:

-   Dane statystyczne odświeżania i oceny kolekcji

-   Podsumowanie kondycji programu Endpoint Protection (w tym liczba klientów chronionych, zagrożonych, nieznanych i nieobsługiwanych)

-   Konfiguracja zasad programu Endpoint Protection

-   Informacje dotyczące wdrażania aktualizacji oprogramowania (część wdrożenia przeznaczone z klienta do czasu UTC, wymagane i opcjonalne i silent i pomijania ponownego uruchomienia)

-   Ogólna zgodność wdrożeń aktualizacji oprogramowania

-   Informacje dotyczące harmonogramu oceny reguły wdrażania automatycznego

-   Liczby i kody błędów wdrażania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba nieaktywnych klientów w kolekcjach wdrożeń aktualizacji oprogramowania

-   Liczba grup, które wygasły aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba aktualizacji oprogramowania na pakiet

-   Procent powodzenia skanowania aktualizacji oprogramowania

-   Minimalna/maksymalna/średnia liczba godzin od ostatniego skanowania aktualizacji oprogramowania

-    Aktualizacja oprogramowania zsynchronizowane przez punkt aktualizacji oprogramowania
-    Ustawienia zgodności: Szczegóły konfiguracji szablonu SCEP oraz sieci VPN i Wi-Fi zasad zgodności

-    Typ zasady dostępu warunkowego EAS (blok lub kwarantanny) dla urządzeń zarządzanych przez usługę Intune

-   TOP 50 procesorów w środowisku

-   Pakiet konfiguracji DCM użycia programu System Center Configuration Manager

-   Kod produktu MSI (typowe aplikacje, które wdrażania klientów)

-   Podsumowanie kondycji ATP

-   Błędy instalacji klienta szczegółowe wdrożenia

- ***[New] *** Sklep Windows dla szczegóły aplikacji biznesowych (Lista agregacji zsynchronizowano aplikacji, w tym AppID stanie online lub do trybu offline i liczby całkowitej zakupionych licencji)

